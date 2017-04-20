---
layout: post
title: Switching from LESS to SASS with the Strangler Pattern
---

- **Developer:** We have to switch from [LESS](http://lesscss.org/) to [SASS](http://sass-lang.com).
- **Product Owner:** Ok, what does that mean?
- **Developer:** We have to rewrite all our CSS.
- **Product Owner:** Nope, not gonna happen!

Everyone of us has had a similar conversation with his PO. And we all know he's right from an economic perspective. In general rewriting a medium to big CSS code base in one step is a bad idea. Trust me, I did it before. It does not deliver immediate customer value, eats up a lot of time and involves ages of your favorite activity - browser testing.

Nevertheless there might be more than one good reason from a developer perspective to switch to a new technology, a new language or a new tool. Higher productivity, easier coding, better scalability - you name it. So I asked myself how can I make this process more agile, convince my PO and prevent being stuck with our current LESS stack?

## The Strangler Pattern
When [Sam Newman](http://samnewman.io) gave a workshop on microservices at Stylight, he mentioned the [Strangler Pattern](https://www.martinfowler.com/bliki/StranglerApplication.html) as a way to move from a monolith to microservices. The name refers to the tactics of strangler trees which use other trees to grow and in the end kill their hosts.

Transferred to the programming world this means: Instead of rewriting the monolith all at once, pick one functionality at a time and put it into a microservice. Repeat this step a few times and you will end up with a lot of microservices and an empty monolith. This approach removes a lot of risk and gives you steady value.

So I started wondering if this could also be helpful to switch from LESS to SASS in the frontend stack. My idea looked like this:

![Strangler Pattern: Approach to switch from LESS to SASS]({{ site.baseurl_images }}/images/strangler-pattern-less-to-sass.jpg)

In words: The LESS architecture is our host and the freshly added SASS architecture our strangler.

With this approach we get a blank slate for our SASS architecture. What a great chance to introduce some helpers and tools for a maintainable, scalable frontend architecture. Applying [linting](https://en.wikipedia.org/wiki/Lint_(software)) to your existing CSS can be intimidating and frustrating, I know. But we start from scratch now, this means zero linting errors and not thousands. Talking about best practices, introducing a naming convention like [BEM](http://getbem.com) also helps for great code quality. Altogether this even convinced our PO and we took the idea for a ride.

## Learnings
While the approach helped our website team to switch to SASS easily without blocking one or two sprints, we also found some points to consider:
- **Two at a time:** You will have to support two technologies side by side for a while. To switch from LESS to SASS this is easy, since nothing happens at runtime. For other technologies or tools this might not be the case.
- **Don’t be lazy:** You must build new features with the new technology, otherwise the final switch will never happen.
- **The final step:** Not every component of the CSS gets constantly rewritten, especially basics like the grid. Don't be restless, use the pattern until the LESS-rest is small enough to tackle in a regular ticket.

The approach is definitely not a silver bullet for all technology switches, but to make the transition from LESS to SASS it works really well. It enables you to keep your tech stack up to date without sacrificing too much time. And in case you run into unconsidered problems with the new technology, switching back is easy at any point of time.
