# Misc

- https://glebbahmutov.com/blog/mock-graphql-with-lunar-in-cypress-tests/

# Tools

- https://github.com/bahmutov/as-a
- [Mailosaur Cypress Commands: Test email and SMS messages with Cypress](https://github.com/mailosaur/cypress-mailosaur)

# Testing Strategies

## [Data Seeding Strategy](https://docs.cypress.io/guides/getting-started/testing-your-app.html#Seeding-Data)
* Execute npm Tasks
> If you’re running node.js on your server, you might add a before or beforeEach hook that executes an npm task.
```
describe('The Home Page', function () {
  beforeEach(function () {
    // reset and seed the database prior to every test
    cy.exec('npm run db:reset && npm run db:seed')
  })

  it('successfully loads', function() {
    cy.visit('/')
  })
})
```
* Exposing Routes **Only For Tests**, this is something that should be supported on the backend. The idea is to expose some routes only for tests purposes.

# Tips
* Shortcut for submitting a form.
```
    // {enter} causes the form to submit
    cy.get('input[name=password]').type(`${password}{enter}`)
```

# References
* [Testing Strategies](https://docs.cypress.io/guides/getting-started/testing-your-app.html#Testing-Strategies).
