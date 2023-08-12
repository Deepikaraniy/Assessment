package stepdefinitions;

import io.cucumber.java.en.*;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import pages.MainPage;

public class StepDefinitions {

    WebDriver driver = new ChromeDriver();
    MainPage mainPage = new MainPage(driver);
    driver.manage().window().maximize();

    driver.findElement(By.xpath("//input[@name='location']")).SendKeys();
    public void iAmOnThePage(String url) 
    {
        driver.get("http://www.nsw.gov.au/visiting-and-exploring-nsw/walks-near-me/map");
    }

    @When("^I enter \"([^\"]*)\" in the search box$")
    public void iEnterInTheSearchBox(String location)
    {
        mainPage.enterSearchLocation("Haymarket");
    }

    @And("^I select \"([^\"]*)\" from auto-suggestion$")
    public void iSelectFromAutoSuggestion(String suggestion)
    {
        mainPage.selectAutoSuggestion("Haymarket NSW, Australia");
    }

    @And("^I click the \"([^\"]*)\" button$")
    public void iClickTheButton(String button)
    {
        mainPage.clickButton("Open Space");
    }

    @Then("^I should see result pins on the map$")
    public void iShouldSeeResultPins() 
    {
        // Add assertion to validate the presence of result pins on the map
    }

    @When("^I check the \"([^\"]*)\" checkbox$")
    public void iCheckTheCheckbox(String checkbox)
    {
        mainPage.checkCheckbox("Apply filters");
    }

    @Then("^I should see only open space pins on the map$")
    public void iShouldSeeOnlyOpenSpacePins()
    {
        // Add assertion to validate the presence of only open space pins on the map
    }

    @After
    public void afterScenario()
    {
        driver.quit();
    }
}
