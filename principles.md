# Principles

It's important to remember:
- We are all working towards the same end goal;
- We are all human which means that we are not infallible;

## Care less, care appropriately

No one cares about your code more than you do.

It's important to pick the right battles, not everything needs to be a point of contention. Be humble, be objective, and be less selfish as there is always a bigger picture to look at.

## Think about the bigger picture

Code itself is unimportant: it's a means to an end. We need to be able to understand the business cost and value of the work we produce.

## Expect and accommodate change

Everything is subject to change and we should be ready for that. Whether it is a change in scope for a feature or an existing piece of functionality you spent a decent amount of time on, change is inevitable and we need to be OK with that.

## The simplest option is usually the best

Simpler code is usually faster and cheaper to implement and it is less likely to fail or break in unexpected ways.

More importantly it is easier for other developers to understand which reduces the cognitive overhead when working at scale, making it easier for other developers to reason about, maintain, debug, and iterate on.

## Reduce the number of moving parts

Every moving part is a potential point of failure. For every layer added to a feature you are inviting the chance for something to go wrong. By removing as much as we can when we iterate we can work towards reducing this risk.

It may even be beneficial to reduce the number of features if we find they simply aren't being used by customers.

This also applies to new features as it may have something that could be useful in the future. In order to reduce complexity we shouldn't extract this as a component/utility until it is actually needed. By making these assumptions too early we could end up maintaining something that tries to do more than is reasonable.

## Good enough today is better than perfect tomorrow

They key questions to ask are "Does it work?" and "Does it meet the business requirements?". If the code quality checks pass and it is well tested then it can be considered complete.

We should measure features by their business value. If we spend a long time working out and building for all of the edge-cases and the feature doesn't work for customers then that time has effectively been wasted. By getting that feedback earlier we can better direct our time and resources to things that will really have a positive impact.

## Don't design a system around edge-cases

We should be building for the most common scenarios and not let the majority lead the minority. Working with others in the business will give us a clear understanding of the problem we are trying to solve. Edge-cases that this brings up should be solved separately.
