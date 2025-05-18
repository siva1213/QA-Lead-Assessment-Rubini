# QA-Lead-Assessment-Rubini Part 3 answers

1. How you would approach testing a mobile application on both iOS and
Android? 
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


2. Key differences between mobile and web testing

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
