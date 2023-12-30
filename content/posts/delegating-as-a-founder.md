---
title: "Delegating as a technical startup founder"
date: 2023-12-25T22:01:15+10:00
draft: false
---

### Intro

In 2022 I spent 5 months building [Bree](https://www.linkedin.com/company/bree-services/). Bree helped people get their clothes altered from the comfort of their own home, it was yet another 'Uber for X' startup. It consisted the following apps:

- Customer app to order clothing alterations/repairs
- Merchant app to view and manage current alterations/repairs
- Ruby on rails api backend with postgres as the data store

FWIW the main focus of this blog post is sharing the tradeoffs we encountered delegating compared to building our own technical solutions. What's better for you might depend on your individual circumstances and the problem you're trying to solve but in general I'd recommend delegating due the the reasons mentioned below.

### What and why

A common example for most apps/websites is authentication. Generally founders and technical leads have a few options:

- Use an auth provider like Okta, Google or Twilio where authentication is a matter of making API calls to the relevant service
- Use a prebuilt package which fits well with an existing codebase of choice e.g [Devise](https://github.com/heartcombo/devise) for Rails
- Roll your own

We learnt the hard lesson that building your own solution is complicated and time consuming. Our decision was based on the following factors:

- We'd have better control over our customers data
- We won't have to migrate from a third party authentication system to our own system which would save us substantial cash/time in the future
- Our asumption was we won't be spending a lot of time building a lean authentication layer
- Using a third party service would couple our data models with a third party authentication provider(in hindsight this can be avoided)
- The system would be purpose built and making future changes would be easier than altering an existing third party solution
- The system would run on our own infrastructure and we'd avoid paying more to third party services extending our startups runway(amount of cash left to run the business)
- It'd be a good learning curve for developers and any code could be referenced/reused in a future project

Here's why the above approach didn't work:

- Instead of spending time solving problems which were more critical to our customers/merchants, we spent the time building something which was already available via plug and play
- Instead of paying with cash, we paid with our time and energy
- As always the case in software engineering, it ended up taking more time than we anticipated
- After the system was built, we had to spend more time handling solving edge cases and fixing bugs

You could argue that importing an existing package could easily be substituted with rolling our own solution. I'd partially agree with that but these packages come with a lot more than just a lean authentication layer. In addition, these packages assume your data model to "look a certain way" and need to be customised to support your use case. IMO the time you'd spend doing that, might as well build a lean auth layer and extend it over time to cater for your scenario.

### Conclusion

That's all for this blog post, feel free to reach out if you agree/disagree with any of the above. And in case if you were wondering what happened to Bree, we failed as most startups do and I'll be sharing more of our story in the future but I'd argue I learnt so many lessons building a startup and I won't trade it with anything else 😀
