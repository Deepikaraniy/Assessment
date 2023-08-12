package stepdefinitions;

import io.cucumber.java.en.*;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import pages.MainPage;

public class StepDefinitions {

    WebDriver driver = new ChromeDriver();
    MainPage mainPage = new MainPage(driver);

    @Given("^I am on the \"([^\"]*)\" page$")
    public void iAmOnThePage(String url) {
        driver.get(url);
    }

    @When("^I enter \"([^\"]*)\" in the search box$")
    public void iEnterInTheSearchBox(String location) {
        mainPage.enterSearchLocation(location);
    }

    @And("^I select \"([^\"]*)\" from auto-suggestion$")
    public void iSelectFromAutoSuggestion(String suggestion) {
        mainPage.selectAutoSuggestion(suggestion);
    }

    @And("^I click the \"([^\"]*)\" button$")
    public void iClickTheButton(String button) {
        mainPage.clickButton(button);
    }

    @Then("^I should see result pins on the map$")
    public void iShouldSeeResultPins() {
        // Add assertion to validate the presence of result pins on the map
    }

    @When("^I check the \"([^\"]*)\" checkbox$")
    public void iCheckTheCheckbox(String checkbox) {
        mainPage.checkCheckbox(checkbox);
    }

    @Then("^I should see only open space pins on the map$")
    public void iShouldSeeOnlyOpenSpacePins() {
        // Add assertion to validate the presence of only open space pins on the map
    }

    @After
    public void afterScenario() {
        driver.quit();
    }
}
