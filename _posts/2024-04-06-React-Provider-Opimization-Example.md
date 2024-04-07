---
date: 2024-04-06T12:07:50.377Z
author: Stefan Hayden
title: React Context Provider Optimization
layout: post
permalink: /blog/2023/12/09/ract-context-provider-optimization/
categories:
  - web
---

React `createContext` is a powerful way to to use react to comunicte between components
but there are a lot of easy mistakes to be made that will slow down your app. From
memoizing everything to seperating component with hooks and components with UI. 

Yet even if you follow all of thopse patterns you can still find your app rendering 
components that could be expensive to render.

This is because providers trigger renders any time they render. It does not matter if a hook or 
parent triggers them to render or if it passes in a memoized value. If a provider
renders it will trigger *anything* subscribed to it with `useContext`.

Consider this provider:

{% highlight JSX %}
{% raw %}
  const [activeModal, setActiveModal] = useState<string>('none');
  const show = useCallback((activeModal: string) => setActiveModal(activeModal), []);
  const value = useMemo(() => ({ activeModal, show }), [activeModal, show]);
  return (
  <ModalContext.Provider value={value}>
    {props.children}
  </ModalContext.Provider>
  );
{% endraw %}
{% endhighlight %}

Above the provider has two values. One to know what the current `activeModal` is. 
The other, `show`, will let compoents around the appo set a new `activeModal`.

**Because the both values share one prodiver ALL compoents who acess the `show` function will render when ANY component calls `show()`.**

When I learned that dozens of compoents were getting rendered simply because they 
wanted option of possible calling `show()` I was a little shocked.
Fixing this is not imediatly obvious. Memoization can not save you and this might 
make you start to look at react state libraries. But there is a solution that is architectural.


{% highlight JSX %}
{% raw %}
  const [activeModal, setActiveModal] = useState<string>('none');
  const show = useCallback((activeModal: string) => setActiveModal(activeModal), []);
  return (
  <ModalActionContext.Provider value={show}>
    <ModalContext.Provider value={activeModal}>
      {props.children}
    </ModalContext.Provider>
  </ModalActionContext.Provider>
  );
{% endraw %}
{% endhighlight %}

With values that change seperated from function that do not change now any component can access the `show()`
funtion and never have it trigger a re-render.

You can play with this below. The red components on the left only use one provider and calling 
`show()` or `hide()` causes all red components to render everytime. On the right the green components are 
broken in two providers and calling `show()` or `hide()` only renders the componets that need to know the `activeModal`.
It doesn't even trigger a render on the component with the button!
{% raw %}
<iframe src="/react/React-Provider-Opimization-Example/" height="930" width="100%" allowfullscreen="" frameborder="0"></iframe>
{% endraw %}
[Play with this code on codesandbox.io](https://codesandbox.io/p/github/stefanhayden/React-Provider-Opimization-Example/main)

Seperating the values and functions is a great start and can save many renders around the aplication. 
Depending on the data you can think of more ways to seperate data. If some values update every time 
and others only sometime then it might make sense to break those in to seperate providers as well.