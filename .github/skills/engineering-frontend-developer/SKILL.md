---
name: engineering-frontend-best-practices
description: Applies reusable, production-grade frontend engineering best practices across frontend frameworks and projects. Covers architecture, component design, maintainability, performance, accessibility, security, API integration, responsive UI, testing and code quality. Use whenever designing, implementing, refactoring or reviewing frontend applications.
---

# Engineering Frontend Best Practices

## 1. Mission

Ensure frontend applications are scalable, maintainable, secure, responsive, accessible, performant and easy to extend.

Apply these standards across projects regardless of frontend framework, programming language, UI library or business domain.

Do not assume a specific technology. First inspect the repository and identify its actual frontend stack.

## 2. Technology Discovery

Before starting any frontend work:

- Identify the frontend framework and version.
- Identify the programming language and version.
- Inspect the existing folder structure.
- Identify the build tool and package manager.
- Identify routing and state management libraries.
- Identify UI frameworks and component libraries.
- Identify API integration patterns.
- Identify existing authentication and authorization mechanisms.
- Inspect existing coding conventions and reusable components.
- Identify testing and code quality tools.

Never introduce a new technology without evaluating existing project capabilities.

## 3. Architecture and Project Structure

Follow a modular, feature-oriented architecture.

Best practices:

- Organize code by business feature or domain.
- Separate UI components, business logic, API services and utilities.
- Keep components focused on a single responsibility.
- Avoid unnecessarily large components.
- Prefer reusable components over duplicated implementations.
- Separate shared components from feature-specific components.
- Keep application configuration centralized.
- Avoid circular dependencies.
- Maintain clear dependency boundaries.
- Avoid unnecessary abstractions and overengineering.

Prefer this conceptual structure:

```text
src/
  app/
    routes/
    providers/
    configuration/

  features/
    feature-name/
      components/
      hooks/
      services/
      types/
      validation/
      pages/

  components/
    common/
    layout/
    forms/

  services/
    api/
    authentication/

  hooks/
  utils/
  types/
  constants/
  assets/
  styles/
```

Adapt the structure to the selected framework and project size. Do not force this exact structure onto every project.

## 4. Component Development

Follow these principles:

- Build small, reusable and independent components.
- Use meaningful component names.
- Keep components focused on presentation or a clearly defined responsibility.
- Separate business logic from presentation when appropriate.
- Avoid unnecessary prop drilling.
- Avoid excessive component nesting.
- Define clear component interfaces.
- Use composition instead of excessive conditional rendering.
- Avoid duplicating UI logic.
- Keep reusable components configurable without making them overly complex.
- Use consistent naming conventions.

For React:

- Prefer functional components and hooks.
- Follow the Rules of Hooks.
- Avoid unnecessary useEffect.
- Use custom hooks for reusable stateful logic.
- Avoid unnecessary memoization.
- Use stable and meaningful list keys.
- Avoid directly manipulating the DOM when React provides an appropriate mechanism.
- Use Error Boundaries for appropriate error isolation.
- Avoid defining components unnecessarily inside other components.

## 5. Type Safety and Code Quality

- Prefer strong typing over loosely typed implementations.
- Avoid `any` unless there is a documented justification.
- Define interfaces and types for API contracts.
- Use appropriate null and undefined handling.
- Avoid unsafe type assertions.
- Use consistent naming conventions.
- Remove unused variables, imports and functions.
- Avoid deeply nested conditional logic.
- Extract complex business logic into testable functions.
- Use constants or enums appropriately.
- Follow existing linting and formatting standards.
- Keep functions focused and readable.

For TypeScript projects:

- Enable strict type checking where feasible.
- Use type-safe API responses.
- Define reusable domain types.
- Avoid unnecessary duplication of type definitions.
- Use discriminated unions for complex state where appropriate.

## 6. State Management

Choose state management based on actual application requirements.

Distinguish between:

- Local component state.
- Shared application state.
- Server/API state.
- URL and navigation state.
- Form state.

Best practices:

- Keep state as close as possible to where it is used.
- Avoid unnecessary global state.
- Avoid duplicating server state in multiple places.
- Use established state management libraries when complexity justifies them.
- Keep state updates predictable.
- Handle loading, success, empty and error states.
- Avoid unnecessary re-renders.

Do not introduce a global state management library for simple applications.

## 7. API Integration

Follow a consistent API integration architecture.

- Centralize API client configuration.
- Keep API calls outside presentation components where practical.
- Use reusable API services.
- Define request and response types.
- Handle HTTP errors consistently.
- Implement appropriate timeout and cancellation behaviour.
- Handle authentication token lifecycle securely.
- Avoid exposing secrets in frontend code.
- Avoid duplicate API requests.
- Handle loading, empty, success and failure states.
- Implement pagination and filtering consistently.
- Validate critical data on the server, even when frontend validation exists.

Never assume frontend validation provides security.

## 8. UI/UX and Design Standards

Maintain a consistent design system across the application.

- Use consistent typography.
- Maintain standard spacing and sizing.
- Use a consistent colour palette.
- Follow reusable design tokens where appropriate.
- Maintain consistent buttons, forms, tables and dialogs.
- Prefer clear navigation.
- Provide meaningful success and error feedback.
- Use confirmation for destructive actions.
- Avoid unnecessary animations.
- Maintain visual hierarchy.
- Avoid inconsistent layouts across different modules.
- Design for usability before adding visual complexity.

The interface should look professional, modern and consistent.

## 9. Responsive Design

Every user-facing screen should be evaluated across:

- Desktop.
- Laptop.
- Tablet.
- Mobile.

Best practices:

- Use responsive layouts.
- Avoid unnecessary fixed widths.
- Prevent horizontal overflow.
- Use responsive images and media.
- Ensure forms remain usable on smaller screens.
- Maintain readable typography.
- Make navigation mobile-friendly.
- Ensure dialogs and tables work on smaller screens.

Do not consider a feature complete if its responsive behaviour has not been checked where applicable.

## 10. Performance Optimization

Focus on measurable performance improvements.

- Avoid unnecessary component re-renders.
- Lazy-load large routes and components when beneficial.
- Optimize image sizes and formats.
- Avoid unnecessary dependencies.
- Split bundles where appropriate.
- Avoid duplicate API requests.
- Use pagination or virtualization for large datasets.
- Avoid expensive computations during rendering.
- Monitor bundle size.
- Use caching appropriately.
- Avoid memory leaks and unmanaged subscriptions.

Do not apply memoization or optimization techniques without a meaningful reason.

## 11. Frontend Security

Security must be considered during every implementation.

- Never store passwords or secrets in frontend source code.
- Never expose private API keys.
- Avoid unsafe HTML rendering.
- Protect against cross-site scripting (XSS).
- Follow secure authentication practices.
- Enforce authorization on the backend.
- Avoid storing sensitive authentication tokens in insecure browser storage.
- Handle session expiry correctly.
- Validate and sanitize untrusted inputs appropriately.
- Do not expose sensitive information through browser logs.
- Follow HTTPS and secure communication requirements.
- Avoid leaking internal API errors to end users.

Frontend route protection is not a replacement for backend authorization.

## 12. Accessibility

Follow WCAG accessibility principles and applicable project standards.

- Use semantic HTML.
- Provide accessible labels for form controls.
- Support keyboard navigation.
- Maintain visible focus indicators.
- Use appropriate ARIA attributes when necessary.
- Ensure sufficient colour contrast.
- Provide meaningful alternative text for images.
- Avoid relying exclusively on colour to communicate status.
- Make dialogs and menus keyboard accessible.
- Ensure form validation errors are accessible.

Prefer native semantic HTML over unnecessary custom controls.

## 13. Forms and Validation

- Use consistent form components.
- Validate required fields.
- Provide clear validation messages.
- Handle server-side validation errors.
- Prevent accidental duplicate submissions.
- Show appropriate loading states.
- Preserve entered data when appropriate.
- Validate data types, formats and boundaries.
- Keep validation rules reusable where appropriate.
- Ensure keyboard accessibility.

Frontend and backend validation rules should remain consistent.

## 14. Error Handling and Logging

- Establish consistent error-handling patterns.
- Handle unexpected application errors.
- Provide user-friendly error messages.
- Avoid displaying stack traces or internal exceptions.
- Log useful diagnostic information without exposing sensitive data.
- Handle network failures and timeouts.
- Provide retry mechanisms only where appropriate.
- Avoid silently swallowing errors.
- Use application-level error boundaries where supported.

## 15. Testing Standards

Follow a layered testing strategy.

- Unit testing for independent business logic.
- Component testing for UI behaviour.
- Integration testing for API and component interactions.
- End-to-end testing for critical user journeys.
- Accessibility testing for important interfaces.
- Responsive testing for relevant screen sizes.

Best practices:

- Test expected behaviour, not implementation details.
- Cover success and failure scenarios.
- Cover boundary conditions.
- Test form validation.
- Test loading and error states.
- Test authorization-related UI behaviour.
- Avoid brittle tests.
- Never remove meaningful tests just to achieve a passing build.

## 16. Code Review and Refactoring

Before considering frontend work complete:

- Review the complete code diff.
- Check for duplicated logic.
- Check component complexity.
- Check naming and readability.
- Check unnecessary dependencies.
- Check performance implications.
- Check accessibility.
- Check security.
- Check responsive behaviour.
- Check test coverage.
- Remove unused code and debugging statements.
- Ensure existing functionality is not unintentionally broken.

Do not perform unrelated refactoring during feature implementation.

## 17. Documentation

Maintain documentation for:

- Frontend architecture.
- Folder structure.
- Reusable components.
- Shared hooks and utilities.
- API integration conventions.
- State management decisions.
- Environment configuration.
- Important technical decisions.
- Setup and development commands.

Keep documentation aligned with actual implementation.

## 18. Definition of Done

Frontend work is complete only when applicable criteria are satisfied:

- [ ] Requirements and acceptance criteria are implemented.
- [ ] Existing architecture and coding conventions are followed.
- [ ] Components are maintainable and reusable where appropriate.
- [ ] Type safety is maintained.
- [ ] API integration and error handling are implemented.
- [ ] Loading, empty, success and error states are addressed.
- [ ] Responsive behaviour is verified.
- [ ] Accessibility requirements are considered.
- [ ] Security considerations are addressed.
- [ ] Relevant tests are added or updated.
- [ ] Build and lint checks pass.
- [ ] No unrelated changes or debugging code remain.
- [ ] Documentation is updated where necessary.
- [ ] Implementation evidence is recorded.

## 19. Framework-Specific Adaptation

Apply framework-specific best practices based on the actual project.

For React:
- Functional components and hooks.
- Component composition.
- React Router where appropriate.
- Appropriate state management.
- TypeScript strictness.
- React Testing Library.
- Performance and rendering best practices.

For Angular:
- Standalone components where appropriate.
- Dependency injection.
- Signals or RxJS based on application requirements.
- Angular forms and routing.
- Angular testing practices.

For Vue:
- Composition API where appropriate.
- Composables.
- Component communication patterns.
- Vue Router and state management.
- Vue testing practices.

Do not apply framework-specific rules to projects that do not use that framework.

## 20. Final Engineering Principles

Always prioritize:

1. Maintainability over unnecessary complexity.
2. Reusability over duplication.
3. Readability over clever code.
4. Security over convenience.
5. Accessibility over visual shortcuts.
6. Performance based on measurement.
7. Consistency over individual coding preferences.
8. Testing over assumptions.
9. Existing architecture over unnecessary rewrites.
10. Business requirements over speculative features.

The goal is not simply to generate frontend code. The goal is to deliver reliable, production-quality frontend software.