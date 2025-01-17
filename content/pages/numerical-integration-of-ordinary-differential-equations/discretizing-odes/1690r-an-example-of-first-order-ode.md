---
content_type: page
learning_resource_types: []
ocw_type: CourseSection
parent_title: 1.2 Discretizing ODEs
parent_type: CourseSection
parent_uid: f239c31a-53e6-28b3-a06a-8e6fff5ed57c
title: 1.2 Discretizing ODEs
uid: 18e3e2fd-45b7-38b5-b9bb-4940200d150a
---

*   {{% resource_link f239c31a-53e6-28b3-a06a-8e6fff5ed57c "\<Discretizing ODEs" %}}
*   {{% resource_link f239c31a-53e6-28b3-a06a-8e6fff5ed57c "1.2.1First-Order ODEs" %}}
*   {{% resource_link 18e3e2fd-45b7-38b5-b9bb-4940200d150a "1.2.2An Example of First Order ODE" %}}
*   {{% resource_link 0baef83e-dfb4-b312-66ed-4f9fe5c876ba "1.2.3Discretization" %}}
*   {{% resource_link 9b1b577d-12e2-e60d-75d3-f8fb6ed609d5 "1.2.4The Forward Euler Method" %}}
*   {{% resource_link ae250ef9-53d1-78da-8810-f88b0aaa6408 "1.2.5The Midpoint Method" %}}
*   {{% resource_link 0baef83e-dfb4-b312-66ed-4f9fe5c876ba "\>Discretization" %}}

1.2.2 An example of first order ODE
-----------------------------------

{{% resource_link 6018b2cc-123e-d80f-52d9-19c7a1393c2e "Measurable Outcome 1.1" "#anchorMO11" %}}, {{% resource_link 6018b2cc-123e-d80f-52d9-19c7a1393c2e "Measurable Outcome 1.3" "#anchorMO13" %}}, {{% resource_link 6018b2cc-123e-d80f-52d9-19c7a1393c2e "Measurable Outcome 1.4" "#anchorMO14" %}}

Ordinary differential equations (ODEs) occur throughout science and engineering.

Free Fall Example
-----------------

A model for the velocity \\(u(t)\\) of a spherical object falling freely through the atmosphere can be derived by applying Newton's Law. Specifically,

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
\\\[m\_ p u\_ t = m\_ p g - D(u) \\label{equ:freefall}\\\]
{{< tdclose >}}
{{< tdopen >}}
(1.4)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

where \\(m\_ p\\) is the mass of the particle, \\(g\\) is the gravity, \\(D\\) is the aerodynamic drag acting on the particle, and \\(u\_ t\\) denotes the derivative of \\(u(t)\\) with respect to time \\(t\\). For low speeds, this drag can be modeled as (recall Unified fluids),

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle D\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\frac{1}{2}\\rho \_ g \\pi a^2 u^2 C\_ D(Re) \\label{equ:freefall\_ drag}\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.5)
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle Re\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\frac{2 \\rho \_ g u a}{\\mu \_ g} \\label{equ:freefall\_ Re}\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.6)
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle C\_ D\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\frac{24}{Re} + \\frac{6}{1 + \\sqrt {Re}} + 0.4 \\label{equ:freefall\_ CD}\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.7)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

where \\(\\rho \_ g\\) and \\(\\mu \_ g\\) are the density and dynamic viscosity of the atmosphere, \\(a\\) is the sphere radius, \\(Re\\) is the Reynolds number for the sphere, and \\(C\_ D\\) is the drag coefficient. To complete the problem specification, an initial condition is required on the velocity. For example, at time \\(t=0\\), let \\(u(0) = u\_0\\). By solving Equation [1.4](javascript: void(0)) with this initial condition, the velocity at any time \\(u(t)\\) can be found.

General ODEs
------------

A general ODE is typically written in the form,

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
\\\[u\_ t(t) = f(u(t),t), \\label{equ:ODE\_ nonlinear}\\\]
{{< tdclose >}}
{{< tdopen >}}
(1.8)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

where \\(f(u(t),t)\\) is the forcing function that results in the evolution of \\(u(t)\\) in time. When \\(f(u(t),t)\\) depends on \\(u(t)\\) in a nonlinear manner, then the ODE is called a nonlinear ODE. Note that in these notes, where clarity permits, we will omit the arguments of functions.

For the example defined by Equation [1.4](javascript: void(0)), the forcing function is,

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
\\\[f(u,t) = g - \\frac{1}{m\_ p} D(u)\\\]
{{< tdclose >}}
{{< tdopen >}}
(1.9)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

From the definition of \\(D(u)\\), \\(f(u,t)\\) is nonlinear in \\(u\\). Note also that in this example, \\(f\\) does not depend on \\(t\\) directly, rather \\(f(u(t),t) = f(u(t))\\).

Linear ODEs
-----------

Although the use of numerical integration is most important for nonlinear ODE's (since analytic solutions rarely exist), the study of numerical methods applied to linear ODE's is often quite helpful in understanding the behavior for nonlinear problems. The general form for a single, linear ODE, is

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
\\\[u\_ t = \\lambda (t) u(t) + g(t), \\label{equ:ODE\_ linear}\\\]
{{< tdclose >}}
{{< tdopen >}}
(1.10)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

where \\(\\lambda (t)\\) is independent of \\(u\\). When \\(\\lambda (t)\\) is a constant, the ODE is referred to as a linear ODE with constant coefficients.

In many situations, the linear ODE is derived by linearizing a nonlinear ODE about a constant state. Specifically, define the dependent state \\(u(t)\\) as a sum of \\(u\_0\\) and a perturbation, \\(\\tilde{u}(t)\\),

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
\\\[u(t) = u\_0 + \\tilde{u}(t). \\label{equ:perturbation}\\\]
{{< tdclose >}}
{{< tdopen >}}
(1.11)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

A linearized equation for the evolution of \\(\\tilde{u}(t)\\) can be derived by substitution of this into Equation [1.8](javascript: void(0)):

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle u\_ t\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle f(u(t),t),\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.12)
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\tilde{u}\_ t\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle f(u\_0 + \\tilde{u}(t),t)\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.13)
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\tilde{u}\_ t\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle f(u\_0, 0) + \\left.\\frac{\\partial f}{\\partial u}\\right|\_{u\_0,0}\\tilde{u}(t) + \\left.\\frac{\\partial f}{\\partial t}\\right|\_{u\_0,0}t + O(t^2, \\tilde{u} t, \\tilde{u}^2).\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.14)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

Note that the last equation is obtained using [Taylor series](http://crosslinks.mit.edu/topic/taylor-series/). Thus, when \\(t\\) and \\(\\tilde{u}\\) are small, the perturbation satisfies the linear equation,

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
\\\[\\tilde{u}\_ t \\approx f(u\_0, 0) + \\left.\\frac{\\partial f}{\\partial u}\\right|\_{u\_0,0}\\tilde{u}(t) + \\left.\\frac{\\partial f}{\\partial t}\\right|\_{u\_0,0}t \\label{equ:ODE\_ linearized}\\\]
{{< tdclose >}}
{{< tdopen >}}
(1.15)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

Comparing Equation [1.10](javascript: void(0)) to [1.15](javascript: void(0)), we see that in this example,

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\lambda (t)\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\left.\\frac{\\partial f}{\\partial u}\\right|\_{u\_0,0},\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.16)
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle g(t)\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle f(u\_0, 0) + \\left.\\frac{\\partial f}{\\partial t}\\right|\_{u\_0,0}t\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.17)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

For the falling sphere problem, a linear ODE can be derived by linearizing about the initial velocity \\(u\_0\\). As shown above, this requires the calculation of \\({\\partial f}/{\\partial u}\\) and \\({\\partial f}/{\\partial t}\\). For the sphere,

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
\\\[\\frac{\\partial f}{\\partial u} = \\frac{\\partial }{\\partial u}\\left\[ g - \\frac{1}{m\_ p} D(u(t))\\right\] = -\\frac{1}{m\_ p}\\frac{\\partial D}{\\partial u}\\\]
{{< tdclose >}}
{{< tdopen >}}
(1.18)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

The value of \\({\\partial D}/{\\partial u}\\) is

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\frac{\\partial D}{\\partial u}\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\frac{\\partial }{\\partial u}\\left\[ \\frac{1}{2}\\rho \_ g \\pi a^2 u^2 C\_ D(Re) \\right\],\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.19)
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle =\\)
{{< tdclose >}}
{{< tdopen >}}
\\(\\displaystyle \\rho \_ g \\pi a^2 u C\_ D(Re) + \\frac{1}{2}\\rho \_ g \\pi a^2 u^2 \\frac{\\partial C\_ D}{\\partial Re}\\frac{\\partial Re}{\\partial u},\\)
{{< tdclose >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
(1.20)
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

and \\({\\partial C\_ D}/{\\partial Re}\\) and \\({\\partial Re}/{\\partial u}\\) can be found from their definitions. Also, since \\(f\\) does not directly depend on \\(t\\) for this problem, \\({\\partial f}/{\\partial t} = 0.\\)

BackDiscretizing ODEs ContinueDiscretization