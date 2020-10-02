---

<!-- .slide: id="proxy" -->
Patron "Proxy"

-- 

## Patron Proxy (GoF)
- Accès direct à un objet est indésirable ou est impossible
- Solution:
  - objet proxy
  - substitut à un objet
  - implémente la même interface
  - ajoute un niveau d’indirection

--

- Proxy
- Design Patterns, Gamma, Helm, Johnson &amp; Vlissides, 1995

![Picture 3](gof_proxy_p)
![image](/assets/LOG210-08-04-patron-proxy.pptx/image1.jpeg)

<img width='100' height='100' data-src='gof_proxy_p'>Picture 3</img>


--


- Patron Proxy (GoF)
- fig 35.12 p 593
- «interface»
- ISubjectInterface
- foo()
- RealSubject
- foo()
- {
- ... pre-processing
- realSubject.foo()
- ... post-processing
- }
- Client
- subject : ISubjectInterface
- doBar()
- 1
- 1
- 1
- 1
- Proxy
- realSubject : ISubjectInterface
- foo()
- {
- ... whatever
- subject.foo()
- ... whatever
- }
- subject actually
- references an
- instance of Proxy,
- not RealSubject
- "realSubject" will actually reference an
- instance of RealSubject

--

# **[Retour au patron GOF](#gof)** - retour au patron GOF
