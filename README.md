# tests.auth
describe('empty spec', () => {
  it('Log in with valid credentials', () => {
    cy.visit('/user/login')

    cy.get('#normal_login_email')
      .type('s...a@gmail.com')
    cy.get('#normal_login_password')
      .type('m....1')
    cy.get('[type=submit]')
      .click()

    cy.location('pathname')
      .should('include', 'profile')
    cy.get('.ant-avatar-square')
      .should('be.visible')
  })
  it('Log in with invalid credentials', () => {
    cy.visit('/user/login')

    cy.get('#normal_login_email')
      .type('snehoda@gmail.com')
    cy.get('#normal_login_password')
      .type('merdoc1982')
    cy.get('[type=submit]')
      .click()

    cy.location('pathname')
      .should('include', '/user/login')
    cy.get('.ant-notification-notice-message')
      .should('be.visible')
        .should('have.text', 'Auth failed')
  })
})
