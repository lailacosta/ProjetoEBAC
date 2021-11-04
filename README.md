# ProjetoEBAC  -- Remover uma transação de entrada



describe("DevFinance", function() {
    it("Remover uma transação de entrada", function() {
        const entrada = "Mensalidade"
        const saida   = "Farda"
        cy.visit("https://devfinance-agilizei.netlify.app/#")

        // get & contains
        cy.get("#transaction .button").click()
        cy.get("#description").type("Mensalidade")
        cy.get("#amount").type("400")
        cy.get("#date").type("2021-11-09")    
        cy.contains('button', "Salvar").click()

        cy.get("#transaction .button").click()
        cy.get("#description").type("Farda")
        cy.get("#amount").type("-100")
        cy.get("#date").type("2021-11-09")    
        cy.contains('button', "Salvar").click()

        cy.get("td.description")
        cy.contains("Mensalidade")
          .parent()
          .find("img[onclick*=remove]")
          .click()

      
        cy.get("table tbody tr").should("have.length", 1)
        

        
    });  
});
