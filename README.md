/// <reference types="cypress" />

//const { data } = require("cypress/types/jquery");

describe("Test of the Assignment1", () =>{
   

      
        beforeEach(function () {
            cy.fixture('./textdata.json').then((text) => {
              this.text = text
            })
          })

    it("Login_Assignment", () => {

        cy.visit("https://www.lookfantastic.com");
 
        cy.get('.responsiveAccountHeader_accountRegister').invoke('show').click({force: true});
        
        cy.get("body").then($body => {
            if ($body.find("div[data-testid='international-overlay-content']").length > 0) {   
            //evaluates as true if button exists at all
                cy.get("div[data-testid='international-overlay-content']").then($header => {
                  if ($header.is(':visible')){
                        cy.get("button[data-testid='international-overlay-close-button']").click();
                } else {
                    //you get here only if button EXISTS but is INVISIBLE
                  }
                });
            } else {
                     
                 assert.isOk('everything','everything is OK');
            }
        }); 

        
        it('Validate successful Login', function () {

            cy.get("div[label='Full Name']").type(this.text.Name);

        })
           
        


        //cy.get("input[type='email']").type("Rakeshwins@gmail.com");
        //cy.get("#password-input-element").type("Rakesh@25494");
        //cy.get("#button-submit-login").click();
        //cy.get('.responsiveAccountHeader_accountRegister').invoke('show').click({force:true});

   
    })
    
    

    })
