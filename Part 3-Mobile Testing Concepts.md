# QA-Lead-Assessment-Rubini Part 3 answers

**1. How you would approach testing a mobile application on both iOS and Android?**

✅ 1. Define Test Strategy/Test plan
a. Understand Requirements
Functional requirements (features, flows)

Non-functional (performance, security, UI responsiveness)

b. Decide Testing Types
Unit Testing

UI Testing

Integration Testing

End-to-End Testing

Regression Testing

Performance and Compatibility Testing

Security Testing

Interruption Testing

✅ 2. Choose Tools and Frameworks
Cross-Platform Automation Tools:
Appium (most popular, supports for both Android/iOS)

Detox (for React Native)

Flutter Driver (Flutter apps)

XCUITest + Espresso (native frameworks for iOS & Android)

CI/CD Integration:
Use GitHub Actions, Jenkins, or CircleCI to run automated tests on real devices/simulators.

✅ 3. Setup Testing Environments
Simulators/Emulators:
Android Emulator (Android Studio)

iOS Simulator (Xcode)

Real Device Testing:
Use device farms (e.g., BrowserStack, Sauce Labs, Firebase Test Lab) to test on a wide range of real devices.

✅ 4. Write Platform-Agnostic Tests (where possible)
Use common test code for shared functionality (with conditional logic if needed).

Keep platform-specific differences isolated.

✅ 5. Perform Manual Exploratory Testing
Validate gestures, push notifications, UI/UX elements.

Test platform-specific behaviors (e.g., back button on Android, swipe gestures on iOS).

✅ 6. Test Device Features
Ensure the app works well with:

Camera, GPS, Microphone, Sensors

Permissions and OS-level settings

Varying network conditions (airplane mode, 3G/4G/5G, no network)

✅ 7. Validate Across OS Versions & Devices
Test on multiple screen sizes and OS versions.

Focus on the most widely used Android devices and iPhone models.

✅ 8. Track and Report Bugs
Use bug tracking tools like Jira, TestRail, or Bugzilla.

Attach screenshots/videos/logs for faster resolution.

✅ 9. Continuously Monitor and Improve
Monitor crash logs via tools like Firebase Crashlytics, Sentry.

Collect user feedback and session recordings.


**2. Key differences between mobile and web testing**

| Mobile App Testing  | Web App Testing |
| ------------- | ------------- |
| These are software programs that are used on mobile devices  | These are software programs that are used on computer  |
| Mobile applications are developed for broader range of users  | Web applications are developed for shorter range of users as compared to mobile applications  |
| New applications can be downloaded from app store/play store  | Applications will be updated on website  |
| It is not easy to create responsive design for small screen devices such as mobile devices, tablets  | It is easy to code relative design for large screen devices such as desktop and laptop  |
| Mobile storage capacity is less than desktop or laptop when it comes to downloading apps and multimedia therefore, sometime it becomes difficult to test mobile apps  | Desktop or laptop has larger storage capacity as compare to mobile  |
| Mobile apps sometimes do not require any internet connection but speed matters, quality of connection matters, speed of LTE connection, etc  | Web app generally requires internet connection to perform any task  |
| It is quite complex and complicated to test mobile apps because of different mobile devices having different and greater number of functionalities  | It is easy and simple to test web applications because of functionality of desktop  |
| Testing team have to check performance of mobile devices on fully charged devices and low charged devices because application that drains battery life gets deleted soon  | There is no such of problem of battery life  |
| One has to consider different screen size, different OEM’s (original equipment manufacturer), storage capacity, etc., in mobile app testing  | One does not consider such things in web app testing  |
| Testing team has to focus on interaction of mobile devices with user’s moves, voice and environment, eye moves, etc., as it offers variety of options to perform operations  | Testing team does not need on interaction of web devices with user’s move, direction of user's attentions, eye moves, etc. as it offers less variety of options to perform operations  |
| "The following are the tools or Frameworks for Mobile App Testing-Appium, Espresso,XCUITest,Xamarin,Robotium and more| "The following are the tools or Frameworks for Web App Testing-Selenium is the most popular one among all other commercial tools,Cypress,Playwright,Katalon Studio and more."  |
| Tablets, peripheral devices like smartwatches, fitness trackers, and even medical devices like heart pacemakers may need to undergo testing  | Mouse, webcams, game controllers, keyboards, and other peripheral devices are tested  |


**3. Tools you would use (Appium, etc.) and why?**

I will choose Appium for mobile app test automation. Here's a more detailed look at why Appium is considered good for mobile app testing:
1. Cross-Platform Compatibility:
Appium supports testing on Android and iOS, allowing testers to write tests once and run them across different platforms with minimal changes. 
2. Multiple Programming Language Support:
Appium can be used with various languages like Java, Python, and Ruby, giving flexibility to testers in choosing their preferred language for writing test scripts. 
3. Testing Different App Types:
Appium can automate testing for native, hybrid, and web applications, covering a wide range of app types. 
4. Testing on Real Devices, Simulators, and Emulators:
Testers can run tests on real devices, simulators, or emulators, allowing them to simulate various user scenarios and device configurations. 
5. Real-time Monitoring and Parallel Execution:
Appium offers real-time monitoring of tests, enabling testers to observe the test execution and identify issues in real-time. It also supports parallel execution, allowing testers to run tests on multiple devices simultaneously, speeding up the testing process. 
6. Integration with Continuous Integration Servers:
Appium can be integrated with continuous integration servers, enabling automated testing as part of the CI/CD pipeline, reducing manual testing effort and speeding up the development process. 
7. No Code Modification Required:
Appium interacts with mobile apps in the same way as end-users, eliminating the need for modifying the application code, ensuring that tests accurately represent real-world scenarios. 
8. Appium Inspector:
Appium comes with an inspector tool that allows testers to visually inspect app elements, identify their properties, and generate test scripts, making it easier to create and maintain test scripts. 
In essence, Appium's combination of features makes it a powerful and efficient tool for automating mobile app testing, helping developers and testers ensure the quality and reliability of their applications. 
9. Open-source Testing Tool:
One of the biggest reasons why customers go for Appium over other mobile app test automation tools is; its open-source framework that encourages testing on simulators, emulators, and real devices. It’s easier for new automation engineers to get their answers via Appium.

**Include example code snippets for basicmobile test scenarios**

1. Launch app and verify home screen
@Test
public void verifyHomeScreenLoaded() {
    MobileElement homeTitle = driver.findElement(By.id("com.example:id/home_title"));
    Assert.assertTrue(homeTitle.isDisplayed(), "Home screen is not displayed");
}
2. Login flow test
@Test
public void testLogin() {
    driver.findElement(By.id("com.example:id/username")).sendKeys("testuser");
    driver.findElement(By.id("com.example:id/password")).sendKeys("password123");
    driver.findElement(By.id("com.example:id/login_button")).click();

    MobileElement dashboard = driver.findElement(By.id("com.example:id/dashboard_title"));
    Assert.assertTrue(dashboard.isDisplayed(), "Login fail and Dashboard is not loaded");
}
3. Scroll down and Click test
@Test
public void scrollToElement() {
    AndroidElement list = (AndroidElement) driver.findElement(By.id("com.example:id/scrollable_list"));
    MobileElement element = driver.findElement(MobileBy.AndroidUIAutomator(
        "new UiScrollable(new UiSelector().scrollable(true)).scrollIntoView(" +
        "new UiSelector().text(\"Target Item\"));"));

    element.click();
}
4. Validate alert and accept
@Test
public void testAlert() {
    driver.findElement(By.id("com.example:id/show_alert")).click();
    MobileElement alertText = driver.findElement(By.id("android:id/message"));
    Assert.assertEquals(alertText.getText(), "This is an alert");

    driver.findElement(By.id("android:id/button1")).click(); // Click OK
}
5. Rotate screen test
@Test
public void rotateScreen() {
    driver.rotate(ScreenOrientation.LANDSCAPE);
    // Validate layout in landscape
    driver.rotate(ScreenOrientation.PORTRAIT);
}
6. App background running test
@Test
public void testBackgroundApp() {
    driver.runAppInBackground(Duration.ofSeconds(5));
    Assert.assertTrue(driver.findElement(By.id("com.example:id/home_title")).isDisplayed());
}
7. Add data(contact) test
import io.appium.java_client.MobileElement;
import io.appium.java_client.android.AndroidDriver;
import org.openqa.selenium.By;
import org.testng.Assert;
import org.testng.annotations.*;

import java.net.MalformedURLException;
import java.net.URL;
import java.util.concurrent.TimeUnit;
import org.openqa.selenium.remote.DesiredCapabilities;

public class AddContactTest {

    AndroidDriver<MobileElement> driver;

    @BeforeClass
    public void setUp() throws MalformedURLException {
        DesiredCapabilities caps = new DesiredCapabilities();
        caps.setCapability("platformName", "Android");
        caps.setCapability("deviceName", "Android Emulator");
        caps.setCapability("appPackage", "com.example.contactsapp"); // Replace with actual package
        caps.setCapability("appActivity", "com.example.contactsapp.MainActivity"); // Replace with actual activity
        caps.setCapability("automationName", "UiAutomator2");

        driver = new AndroidDriver<>(new URL("http://localhost:4723/wd/hub"), caps);
        driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
    }

    @Test
    public void testAddContactSuccessfully() {
        // Click on "Add" button
        driver.findElement(By.id("com.example.contactsapp:id/add_button")).click();

        // Enter contact details
        driver.findElement(By.id("com.example.contactsapp:id/name_input")).sendKeys("Rubini");
        driver.findElement(By.id("com.example.contactsapp:id/phone_input")).sendKeys("1234567890");

        // Submit
        driver.findElement(By.id("com.example.contactsapp:id/save_button")).click();

        // Validate the contact appears in the list
        MobileElement addedContact = driver.findElement(By.xpath("//android.widget.TextView[@text='Rubini']"));
        Assert.assertTrue(addedContact.isDisplayed(), "Contact was not added successfully");
    }

    @AfterClass
    public void tearDown() {
        if (driver != null) {
            driver.quit();
        }
    }
}

