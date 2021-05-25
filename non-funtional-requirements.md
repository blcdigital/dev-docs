# Non-functional requirements

It can be easy to focus on goals of the product, sprint, or ticket but there are common themes that apply to most of the work we do that won't always be captured in the day-to-day task.

The topics here have a material impact on our customers, other developers, and the company itself.

## Performance

The system should be designed and built with an acceptable of performance as a minimum.

This should take in to account things like latency, load, and resource utilisation. Performance can be negatively affected by a number of factors so it should be clear as to what is being measured. These requirements should also evolve as the system does - new features can easily change where the highest load and resource consumption occurs.

## Availability

Sometimes referred to as "uptime", we must ensure the system is available for use as much as possible. Generaaly expressed as a percentage it should also take in to account the Maintainability of the system.

## Maintainability

This defines the time required for the system or one of its components to be fixed due to failure or updated during the normal course of development. For example, if you have 75 percent maintainability for 24 hours, this means that there’s a 75 percent chance the component can be fixed in 24 hours.

For regular releases we should aim for zero downtime deployments and the ability to rollback versions should we encouter issues during this process.

## Security

This requirement assures that data held within the system is protected from certain threats such as unauthorized access.

While a lot of security requirements can and should be made into functional ones this should detail what specific threats must be protected against and what standards or encryption methods should be implemented.

## Compliance

Much like Security a lot of of the legal and regulatory requirements from the system will have a functional aspect. The specific laws that apply and the approaches required to meet them should be detailed here.

## Usability and accessibility

### Usability

Usability assess how easy the user interface is to use. [Neilsen Norman Group](https://www.nngroup.com/articles/usability-101-introduction-to-usability/) evaluates this using five components:

- **Learnability:** How easy is it for users to accomplish basic tasks the first time they encounter the design?
- **Efficiency:** Once users have learned the design, how quickly can they perform tasks?
- **Memorability:** When users return to the design after a period of not using it, how easily can they reestablish proficiency?
- **Errors:** How many errors do users make, how severe are these errors, and how easily can they recover from the errors?
- **Satisfaction:** How pleasant is it to use the design?

### Accessibility

Usability deals with the task based aspect of the system whereas Accessibility is for the ability to use the system at all.

We should endeavor to make a system that is materially usable by as many people as possible. This section should detail things like what Web Content Accessibility (WCAG) standard is being followed and what the testing strategies are (color contrast testing, etc).

### Browser compatibility

The browsers that we support should be based on real data from analytics. If this data is not available then we can use broader customer trends.

#### Grade A

The UI must closely match the designs and all functionality must be present.

- Chrome (includes Android/iOS, latest minus 2)
- Safari (includes iOS, latest minus 2)
- Samsung Internet (latest minus 2)

#### Grade B

The UI should degrade gracefully for unsupported visual elements and all functionality must be present.

- Edge (latest)
- Firefox (latest)
