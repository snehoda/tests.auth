describe('Log in', () => {
  it.skip('Log in with valid credentials', () => {
    cy.visit('/user/login')

    cy.get('#normal_login_email')
      .type('snehoda@gmail.com')
    cy.get('#normal_login_password')
      .type('merdoc1981')
    cy.get('[type=submit]')
      .click()

    cy.location('pathname')
      .should('include', 'profile')
    cy.get('.ant-avatar-square')
      .should('be.visible')
  })
  it.skip('Log in with invalid credentials', () => {
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
  it.skip('‘email’ is not a valid email', () => {
    cy.visit('/user/login')

    cy.get('#normal_login_email')
      .type('ffff')
    cy.contains('\'email\' is not a valid email')
      .should('be.visible')
  })
  it.skip('email is ‘Required’', () => {
    cy.visit('/user/login')

    cy.get('#normal_login_email')
      .type(' ')
    cy.get('input').clear()
    cy.get('input').clear({ force: true })
    cy.contains('Required')
      .should('be.visible')
  })
  it.skip('password is ‘Required’', () => {
    cy.visit('/user/login')

    cy.get('#normal_login_password')
      // .type('2222222')
      .type(' ')
    cy.get('input').clear()
    cy.get('input').clear({ force: true })
    cy.contains('Required')
      .should('be.visible')
  })
})
