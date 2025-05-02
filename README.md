![image](https://github.com/user-attachments/assets/13b8d4c2-d9f7-4eaf-ba14-bdbfcfd394d7)# Assignment-4-User-Testing-with-Selenium---Jose-G-Vallejo-Suvash-Shrestha
**Assignment 4: User Testing with Selenium**

Suvash Shrestha and Jose G. Vallejo

**Table of Contents**

- Introduction
- Part 1: Online Boutique Test
- Part 2: Selenium Tests on MangaPark
  - Test Case 1: Registration Form Input
  - Test Case 2: Manga Navigation & View Change
  - Test Case 3: Login Attempt & Comment Post
- Conclusion and Recommendations

**Introduction**

This report details the work completed for **_Assignment 4: User Testing with Selenium_**. The primary objective was to gain practical experience in automating user interface tests for web applications using Selenium. We utilized **_Selenium IDE_** (a Firefox browser extension) to record, edit, and execute test steps directly within the browser as recommended in the _Assignment4_Selenium_v2.3_ PDF requirements. All of the tests were run on Mozilla Firefox, using the built-in Developer Tools to inspect page elements and construct reliable selectors for automation.

The assignment was divided into two parts. **Part 1** focused on creating a fundamental test script for the **_Online Boutique_** sample web application (deployed locally via Docker/Kubernetes as set up in Assignment 3, accessible at <http://localhost:8080>). This test automated a typical user flow: navigating the site, selecting a product, adding it to the shopping cart, and verifying that the item's price matches the expected value using Selenium IDE assertions.

Additionally, **Part 2** expanded on this experience by requiring three distinct automated tests against a publicly accessible website. As the target site, we chose this website that can host and view manga called Manga Park (v5), which is <https://mangapark.org>. We created three user stories to perform this test case per the assignment requirement. This three different user scenarios were automated using Selenium IDE for Manga Park: (1) verifying that input fields on the user registration (sign-up/login) form accept text input, (2) navigating through manga chapters (including using Next/Previous chapter controls) and changing the reading view mode, and (3) attempting a user login and then trying to post a comment on a manga chapter. All tests in Part 2 were also developed and executed in Firefox via Selenium IDE, employing techniques such as explicit waits’ (e.g. "wait for element visible") to handle dynamic content loading, and verification steps (using commands like assert text, assert value, and assert element present) to validate that the web application behaved as expected.

We observed the Selenium IDE logs and browser outcomes throughout both parts to determine if each step passed or failed. The following sections present each part of the assignment in detail, including the test cases, how they were implemented, and the results with supporting screenshots.

**Part 1: Online Boutique Test**

**Test Scenario:** For Part 1, we automated an end-to-end scenario on the Online Boutique demo e-commerce site. The goal was to verify that adding an item to the cart updates the cart correctly with the right price. The test script opens the Online Boutique homepage, navigates to a product page, adds the product to the shopping cart, and then checks that the cart displays the correct item and price. We used Selenium IDE to record and refine these steps. Key commands included clicking on the product link, clicking the "Add to Cart" button, and then using an assert text command to verify that the cart page shows the expected price for the item added.

Execution was done on our local deployment of Online Boutique (accessible via localhost:8080). We ensured the environment ran before the test and followed the requirements of using the microservices from Assignment 3. Selenium IDE’s recorder captured the navigation and click actions; we then manually added an assertion to validate the cart content. Specifically, after adding the item, the script waited for the cart page to load and then checked that the cart’s item price text matched the selected item price.

![image](https://github.com/user-attachments/assets/face91f2-627a-4d12-8c89-d4ec84340991)

_Figure 1: Online Boutique cart page after adding a "Tank Top" product. The cart shows one item (Tank Top) at price $18.99, plus a shipping fee, for a total of $27.98. The Selenium IDE test verified that the item’s price ($18.99) in the cart matches the expected price._

As shown above, the test case successfully passed the Selenium IDE log. The cart page displays the Tank Top item with a unit price of $18.99, and the subtotal/total reflects this price (plus shipping). The assertion in the Selenium IDE script confirmed the presence of the correct price text on the cart page, indicating that the item was added correctly. The Selenium IDE execution log showed the assertion step passing, and thus the test outcome was PASS for Part 1. This demonstrates that the Online Boutique application’s cart functionality worked as expected for the user who added a single item. Below we will present the screen show of the all passed test cases.

![image](https://github.com/user-attachments/assets/8c42b7bd-caa6-491a-a3bd-8f332ef9657f)
![image](https://github.com/user-attachments/assets/fab3a1fe-3166-45af-abec-7de0adbf63f8)
![image](https://github.com/user-attachments/assets/78bc604c-7fd5-48c3-8741-9c554b4d4aab)
![image](https://github.com/user-attachments/assets/ba94d067-d639-4a82-b038-523d703de101)
![image](https://github.com/user-attachments/assets/560fee82-4093-40d1-8ae7-db993ebc4519)
![image](https://github.com/user-attachments/assets/88cbb797-3d26-43bc-ac78-48250b302830)
![image](https://github.com/user-attachments/assets/d8702214-9af6-48a0-9492-0cce66461303)
![image](https://github.com/user-attachments/assets/c247735a-9abd-43c1-8fd9-148f2e3a0545)
![image](https://github.com/user-attachments/assets/e3cf0a5f-1af4-4c4c-b091-80091465450b)
![image](https://github.com/user-attachments/assets/7a58dd0a-89ee-46dd-bba5-ebe40eb61217)
![image](https://github.com/user-attachments/assets/62e67fba-c834-47b8-9bf5-54e6bbce9132)
![image](https://github.com/user-attachments/assets/9a9a7004-6973-4234-af25-b6fad68e5c14)
![image](https://github.com/user-attachments/assets/4948cdf7-8c5f-4b69-aaee-f77bbb8127b1)
![image](https://github.com/user-attachments/assets/186ef0ca-3c82-4d52-95cd-1eeceb5b878d)
![image](https://github.com/user-attachments/assets/51613cd8-62e2-4d9d-8888-e1b10547d220)

**Part 2: Selenium Tests on Manga Park**

For Part 2, we created three separate test cases on the Manga Park website. Manga Park is a web application for reading manga (Asian and American comic chapters) online. We identified three realistic user scenarios to automate:

- **Test Case 1:** _Registration Form Input_ – Verify that a new user can navigate to the sign-up (registration/login) page and fill in the form fields (e.g., username and password) without issues, confirming that the form accepts the input.
- **Test Case 2:** _Manga Navigation & View Change_—Ensure that a reader can select a specific manga, navigate through its chapters (using next and previous chapter buttons), and change the reading mode (for example, from single-page view to all-page view), verifying that these UI controls work properly.
- **Test Case 3:** _Login Attempt & Comment Post_ – Test the process of attempting to log into Manga Park with given credentials and then posting a comment on a chapter, checking whether the comment submission is handled correctly (in this case, we expect it to fail or be prevented since it’s a test account or not logged in).

All three tests were executed using Selenium IDE in Firefox. We used the recorder to get initial steps and then edited the steps to include assertions for expected outcomes. The following subsections describe each test case, including the user story, the test steps, and observed results (with screenshots).

**Test Case 1: Registration Form Input**

**User Story:** _“As a new user, I want to navigate to the registration page and fill in the registration form fields to verify that the form accepts input.”_

**Test Description:** This test case covers the scenario of a user trying to register (or sign up) on Manga Park. Using Selenium IDE, we automated the steps to click on the **“Sign In”** link (which brings up the login/registration form, since Manga Park combines sign-in and sign-up on the same interface), then enter a username and a password into the form fields. Furthermore, we focused on verifying that the text input fields accept the entries and display them correctly. After typing in a sample username (e.g., “TestDummyJaden9184”) and password (“TestDummyJadenPass9184”) into the form, the script uses assert value commands to check that each field’s value matches what was typed. This confirms that the form input was successfully captured by the browser. We then ended some of the test without clicking a final "Submit" button since our goal was to validate input acceptance.

**Results:** The registration form input test ran successfully. The Selenium IDE execution log indicated that the commands to type into the username and password fields executed without error, and the subsequent assertions on those fields’ values returned **OK**. In other words, the script was able to read back the entered text, verifying it was indeed present in the form. No validation errors were triggered by just entering the data (since we did not submit the form). This means the form allowed the input, meeting the test expectation.

![image](https://github.com/user-attachments/assets/e9ccd4e3-a61b-4db6-abbb-abc9d0007270)

_Figure 2: Selenium IDE log for the Registration Form Input test. The log shows the sequence of commands (open site, click “SIGN IN”, type into username and password fields) and green checks for assert value on both the username (id=uniq) and password fields, indicating the entered text (“TestDummyJaden9184” and “TestDummyJadenPass9184”) was successfully verified._

As shown in the figure, the final test case had no failures. Each step from opening the Manga Park homepage to clicking the sign-in link and typing in the credentials was executed, and crucially, the assertions confirmed that the input values in the form matched the expected strings. This gives confidence that a user can interact with the registration/login form inputs on Manga Park and that those inputs behave normally (text can be entered). Here are the screenshot of all actions taken for this user story:

![image](https://github.com/user-attachments/assets/0cb170ef-0749-430e-b4c9-2d35123c260c)

Below is the manual testing procedure for visiting the website and performing registrations.

![image](https://github.com/user-attachments/assets/c2e6b9f9-e48b-436a-9fa3-4e8537d11a11)
![image](https://github.com/user-attachments/assets/6a49e015-2409-4a76-8d45-072f2341f548)
![image](https://github.com/user-attachments/assets/3fddd18e-53ec-45e9-bbba-5f99a76cddd0)
![image](https://github.com/user-attachments/assets/6a19c4bb-92d7-4d0c-8548-fe36197f3c61)
![image](https://github.com/user-attachments/assets/435d4492-df4b-4653-b47c-87ce328099a2)
![image](https://github.com/user-attachments/assets/2280ad43-c173-4432-afd7-528b3ece2622)
![image](https://github.com/user-attachments/assets/6bd2591b-3511-40e7-85eb-46ab8231ea38)
![image](https://github.com/user-attachments/assets/a8ef76f9-d767-4c8a-a2ce-431382b5d82b)
![image](https://github.com/user-attachments/assets/5ca02896-700d-44ea-81e3-84b7fe3b6582)
![image](https://github.com/user-attachments/assets/4dd125d0-a5b7-4630-9816-ace976c54f02)
![image](https://github.com/user-attachments/assets/4175c1f2-e42f-422e-9432-907abea972a2)
![image](https://github.com/user-attachments/assets/6c045742-f8d9-4ba5-b120-f23c3962fb5c)


We procced to do perform this test in Selenium

![image](https://github.com/user-attachments/assets/c28addfd-1d26-40b0-9de2-d0a07823a089)
![image](https://github.com/user-attachments/assets/89ecb896-1cf2-4447-aa83-dba90e5b6b3d)
![image](https://github.com/user-attachments/assets/266688b6-d26f-4b7e-90f5-e81466e6eed1)
![image](https://github.com/user-attachments/assets/fe72c6a9-11d5-4877-b6f8-a14d2186baff)
![image](https://github.com/user-attachments/assets/7112e7f5-8354-45d7-a74e-32bf12f6d11c)


**Test Case 2: Manga Navigation & View Change**

**User Story:** _“As a reader, I would like to select a particular manga, navigate to a specific chapter, proceed to the next chapter, return to the previous chapter, and adjust the reading view in order to verify that the navigation functionality operates correctly.”_

**Test Description:** This test case simulates a common user journey on a manga reader site: selecting a manga and reading through chapters with different view settings. We automated the following sequence on Manga Park:

1. From the homepage, navigate to a chosen manga title. In our test, we searched for and clicked on the manga “Pick Me Up!” (Infinite Gacha).
2. Click on a specific chapter on the manga’s page (e.g., Chapter 146) to start reading.
3. Once the chapter is open, use the “Prev Chapter” button to return to Chapter 145, then use the “Next Chapter” button to advance to Chapter 146. We employed assert text commands on the chapter title heading to verify that the correct chapter number is displayed after each navigation, ensuring we moved to the intended chapter.
4. Change the reading view mode. Manga Park offers a dropdown for **“load mode”** (page display mode). Initially, it might default to showing one page at a time; we changed this to **“All Pages”** mode (so that all pages of the chapter load in one long scroll). The test used a select command to change the dropdown to "All Pages" and verified the change by checking that multiple page images were present or that the interface reflected the new mode. (For instance, a second page image element can indicate that All Pages mode is active.)

We included appropriate waits (e.g., waiting for the chapter content to load) to account for the site fetching images. The assertions after each action ensured that the page's state matched the expected outcome (chapter titles and number of page images).

**Results:** The Manga navigation and view toggle test was completed, and all verification steps passed. After clicking **Chapter 146**, the page displayed "Chapter 146" as expected. Hitting the Prev button loaded **Chapter 145** (confirmed by an assertion checking the chapter label), and the next button brought us back to **Chapter 146**. Switching the **Load mode** to "All Pages" was successful. Finally, the test verified this by detecting multiple page content elements, meaning the entire chapter’s pages were loaded. An excerpt of the Selenium IDE log showed messages like “Test Passed: Manga navigation and view change successful,” indicating that our final echo/log step was reached without any assertion failing.

![image](https://github.com/user-attachments/assets/b146fc00-1f1d-4804-83b3-2ff8acb2a8b1)

_Figure 3: Manga Park reading interface during the navigation test. In this screenshot, the user views "Pick Me Up! - Chapter 145". The interface shows that_ **_Load mode_** _is set to "All Pages" (meaning all pages of the chapter are loaded), and the navigation buttons for_ **_Prev Chapter_** _and_ **_Next Chapter_** _are visible (with Next Chapter leading to 146). This state was reached after the script navigated chapters and changed the view mode._

The figure above illustrates the application's state after performing the navigation actions. The test case verified that:

- Clicking **Prev Chapter** brought to the previous chapter (145).
- Clicking **Next Chapter** loaded the next chapter, set it back to (146), and updated the heading accordingly.
- Changing the **load mode** to "All Pages" updated the content display (all pages of the chapter are present as one continuous scroll, as opposed to single page mode). The Selenium IDE log showed each assert text check (for chapter titles "Ch.145" and back to "Ch.146") as OK, and the select action to change the view mode was also marked as OK. There were no failures, so we also concluded PASS for this test case. The Manga Park site’s chapter navigation features and view toggling behaved as expected in our automated scenario.

Below is a screenshot of all actions associated with this user story.

![image](https://github.com/user-attachments/assets/6c66e084-713e-49cc-908c-900759ffb285)
![image](https://github.com/user-attachments/assets/fecbc8b8-82ff-476d-ab12-19caac2d505a)
![image](https://github.com/user-attachments/assets/ba50fa20-fe8e-4d39-aa32-09a7921bbe02)
![image](https://github.com/user-attachments/assets/0e941eae-6272-468f-abae-9f968704a734)
![image](https://github.com/user-attachments/assets/512be6f6-912a-44e7-8856-2a4ff067e9b0)
![image](https://github.com/user-attachments/assets/12aa93b7-fe57-461a-8dd4-8423b723ce2a)
![image](https://github.com/user-attachments/assets/aa00b837-62db-457d-95d3-0a7a836586e9)
![image](https://github.com/user-attachments/assets/8cfddaa7-9d2f-458a-8498-340bd024ca73)
![image](https://github.com/user-attachments/assets/0db11958-045c-4db7-bcf6-c32dda0a5e56)
![image](https://github.com/user-attachments/assets/1cc41f31-aa52-4850-9453-c4d92d53d22d)
![image](https://github.com/user-attachments/assets/f58b51f6-6204-4f97-b288-3919e0a6c37d)
![image](https://github.com/user-attachments/assets/8cfa6ad0-bd8f-414f-8dc0-912d4dda9f2b)
![image](https://github.com/user-attachments/assets/91707f46-42e3-48c2-9626-219460a96557)
![image](https://github.com/user-attachments/assets/e952dbd4-2a0e-46e6-a9c8-3ed35157d4d5)
![image](https://github.com/user-attachments/assets/6b9b23bf-dd47-4f1a-908a-35660d2f895d)
![image](https://github.com/user-attachments/assets/64a3a869-2db1-48ef-a652-99dce7781a78)
![image](https://github.com/user-attachments/assets/d0695672-9b08-4357-8b5f-34647d542255)
![image](https://github.com/user-attachments/assets/39adfdf5-7cf9-43f4-a26d-70ce9a764289)
![image](https://github.com/user-attachments/assets/da089f0d-7d3a-4951-a374-83637587004c)
![image](https://github.com/user-attachments/assets/d7071070-462a-4cf8-a383-9e39f3f7258f)
![image](https://github.com/user-attachments/assets/894fab93-8a78-44b6-b0b7-97dc945da78e)

**Test Case 3: Login Attempt & Comment Post**

**User Story:** _“As a registered user, I want to attempt to log in and post a comment on a manga chapter so that I can participate in discussions.”_

**Test Description:** This scenario tests a user’s ability to log into Manga Park and then post a comment (review) on a chapter page or the Title page of the manga. It is a more advanced case that ties authentication and user interaction (commenting) together, and it was somewhat conditional because it depends on having valid credentials. We approached it as follows:

1. Navigate to the **Sign In** page (similarly to Test Case 1) and attempt to log in with a set of credentials (we reused the dummy username _TestDummyJaden9184_ and password from Test 1). Enter the test user’s credentials into the login form (filling in username/email and password, which requires handling dynamic form field IDs via stable selectors) and submit the form. Use an echo command or an assertion (e.g., checking for a user-specific element) to confirm the login's success. After trying to log in with a dummy user, the script navigates to a manga (e.g., **“Reality Quest”** manga page) and then to a specific chapter. On that chapter page, it scrolled to the **Reviews/Comments** section.
2. **Navigate to Manga Page:** After login, ensure the script is on the homepage (click the **Home** link if necessary) and then click on the **Reality Quest** manga title. This opens the manga’s main page, which lists its chapters.
3. Attempt to post a comment: we automated a click on the **“Write My Review”** or comment text box, attempted to type a sample comment (e.g., "Selenium IDE Test Comment!") into the comment field, and then click the **Post/Save** button to submit the comment.
4. Verification: We planned to verify whether the comment appears on the page after submission (using an assert text to search for the comment's content in the list of reviews). Essentially, the final steps were designed to either confirm that the comment was posted (if login succeeded) or detect that it could not be posted. We included an assertion or check for an expected outcome in each case. Finally, we used Echo to check if the test passed.

**Results:** The outcome of this test indicated that the login successfully established a session, allowing the subsequent attempt to post a comment to succeed. The Selenium IDE log for this test shows that the steps for entering the username and password, as well as clicking the login button, were executed correctly. These steps were marked with green checkmarks and an echo message "Test Passed: Login Successful" was logged, reflecting optimism in the script. However, the following steps, where the script attempts to enter the comment and click the submit button, failed. Specifically, the log displays an error when attempting to interact with the submit button for the comment—the element could not be interacted with, likely because the user was not genuinely logged in. The action may have been blocked by the site, or the element might have been absent or disabled. Consequently, the comment text did not appear on the page, resulting in a **FAIL** status for the comment posting section (the Selenium IDE reported 1 failure in the run).

To resolve this issue, we manually clicked into the comment text box (a &lt;div&gt; with contenteditable="true") and typed the comment message, for instance: _“Selenium IDE Test Comment!”_. Next, we waited for the **Save** button (which has the CSS class .btn-primary) to become visible and enabled, then clicked the **Save** button. This action submits the comment. A brief pause (e.g., 2 seconds) is included to allow the submission process to complete. After clicking Save, the script executes a page reload using a run Script command with window.location.reload(). This explicit refresh ensures that the newly posted comment is f_etched from the server and a_ppears in the DOM. Finally, the script uses an assertion to verify that the comment is displayed on the page: a waitForElementPresent (or assertText) with an XPath locator checks for an element containing the text “Selenium IDE Test Comment!”. This confirms that the comment was successfully posted under the logged-in user’s account.

With all the corrections implemented, **Test Case 3** runs to completion without errors. The login step is successful (using robust selectors to handle dynamic form fields), and the subsequent navigation to a chapter page ensures that the comment interface is present. Posting the comment on the chapter page is successful—the **Save** button is clickable and the comment is submitted. The Selenium IDE log from the updated test run shows all steps passing without failures and includes a final echo confirming that both the login and comment posting were completed.

Thanks to these adjustments addressing the XPath and dynamic content issues (ensuring the correct page context for the Save button and using an XPath to locate the dynamic comment text), Test Case 3: Login & Comment Post is now successful. The test demonstrates a complete end-to-end scenario: user login followed by a comment submission on a manga chapter, with Selenium IDE proficiently handling dynamic page elements and content updates. We have provided the attachment of the screenshot performed during this phase as shown below.

![image](https://github.com/user-attachments/assets/595f583f-d29c-49f9-8a29-3b37be61f28f)
![image](https://github.com/user-attachments/assets/407156ce-c594-4226-bee1-48239b8315b6)
![image](https://github.com/user-attachments/assets/cb567d4a-d2bd-41ee-8794-df40d916a596)
![image](https://github.com/user-attachments/assets/569481bb-505a-4dac-972d-090ffbbcac9c)
![image](https://github.com/user-attachments/assets/52d8ca23-1adb-44a2-aca8-093b7a204251)
![image](https://github.com/user-attachments/assets/4cc90f39-46ee-4c6a-b642-e196fd4f377d)
![image](https://github.com/user-attachments/assets/42f452ef-f9d0-40ca-ada9-c853ae3b7439)
![image](https://github.com/user-attachments/assets/1d212594-e0d3-496b-af52-d726fce4d92a)
![image](https://github.com/user-attachments/assets/d91da9c4-d3c3-4477-b526-7e614736e9f6)
![image](https://github.com/user-attachments/assets/c06da22b-a28d-43cd-a645-e9b871917c46)
![image](https://github.com/user-attachments/assets/74319eae-bb60-4a7f-b302-2fc005f3bffa)
![image](https://github.com/user-attachments/assets/7761e4ff-4967-4935-a7e4-a6519de3cd45)
![image](https://github.com/user-attachments/assets/9763b9ab-7847-4cc1-bd0c-e90a4b2b1d2a)

**Conclusion and Recommendations**

**Conclusion:** This assignment provided significant hands-on experience with the fundamentals of automated UI testing using Selenium IDE. One key learning outcome was understanding how to translate manual test cases into automated scripts by identifying relevant UI elements and simulating user interactions such as clicks, text entry, and dropdown selections. We saw first-hand the importance of robust element locators (CSS selectors, XPath, etc.) – for example, finding unique identifiers for buttons or input fields – and the challenges posed by dynamic web content. In the Manga Park tests, some elements like the comment box or navigation buttons required careful inspection and sometimes adding waits to ensure elements were present before interacting, underscoring the need for handling timing issues in automation.

From an **integration testing** perspective, our Selenium IDE tests validated the end-to-end behavior of the applications at the user interface level. In Part 1, the test confirmed that the Online Boutique’s front end and backend worked together so that when a product is added on the UI, the cart service and UI update the cart correctly. In Part 2, the tests checked that those front-end controls on Manga Park (chapter navigation, mode switching) correctly triggered the expected application responses – these involve the front-end interacting with the back-end (for example, loading the next chapter’s data via APIs, or requiring a logged-in session to post a comment). While our tests were UI-centric, they indirectly exercised the integration points between the UI and underlying backend services or APIs (e.g., the login attempt hitting an auth API, the manga content loading via some content API). We also observed how UI tests differ from direct API tests: UI tests are generally slower and more brittle in the face of interface changes, and they can only test what is exposed through the UI. They cannot easily cover edge cases or internal logic that isn’t visible to the user. Nevertheless, they are valuable for validating complete user workflows and ensuring all system parts (frontend, backend, network) work together as intended for common scenarios.

We also learned practical skills with Selenium IDE such as implementing explicit waits and using assertions effectively. Adding commands like wait for element visible improved our test reliability by pausing steps until the application was ready, and assertions like assert text and assert value ensured that our tests not only perform actions but also verify outcomes automatically. By the end of these exercises, we could see how a well-designed automated test can serve as a regression check – for example, if a future change broke the “Add to Cart” functionality, our Part 1 test would fail and immediately signal a problem.

**Recommendations:** One recommendation to improve this assignment is to encourage students to try exporting their Selenium IDE tests to code (Selenium WebDriver scripts in Python/Java, etc.) as an extension of the assignment. This would give a deeper insight into how the recorded steps translate into code and how integration tests could be run more flexibly, programmatically. It would also highlight the differences between using the Selenium IDE tool and writing a scripted test, reinforcing understanding of underlying Selenium commands.

Overall, the assignment was very effective in introducing UI testing. It taught us how **automated integration tests** can catch issues in workflows (for example, if the cart total didn’t update, or if chapter navigation was broken, our tests would flag it). It also highlighted the interplay between client-side actions and server-side responses. By completing this assignment, we are better prepared to create automated test suites for web applications and have a solid foundation to build on (such as transitioning to more advanced frameworks or integrating these tests into a continuous integration pipeline).
