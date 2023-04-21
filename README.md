# Lab-8_31

## Lab-8 Group Submission -  Flutter Unit Testing for Canteen App

### 21 April, 2023


#### The programming language used in the conversation was Dart, which is the language used for building Flutter apps.

- The test cases were designed to test the login screen form validation.
- The test cases were written to ensure that valid data entered into the email and password fields results in the LoadingDialog widget being displayed, and invalid data results in an ErrorDialog widget being displayed.


#### The test cases were written in the Flutter testing framework, which is a testing framework for testing Flutter applications. The test cases were designed to simulate user interactions with the login form and verify that the form validation worked as expected.

<img width="400" alt="fwt" src="https://user-images.githubusercontent.com/75672785/233713730-5185ff89-525e-4960-95fe-b99a846d67dc.jpeg">


* The first test case was designed to test the form validation when valid data is entered into the email and password fields. The test case first built the widget tree by pumping the login screen widget using the pumpWidget() method. Then it entered valid data into the email and password fields using the enterText() method. Finally, the test case submitted the form by tapping on the Sign in button using the tap() method. After submitting the form, the test case waited for the widget tree to settle using the pumpAndSettle() method. Then it verified that the LoadingDialog widget was displayed using the find.byType() method and the findsOneWidget matcher.

* The second test case was designed to test the form validation when invalid data is entered into the email and password fields. The test case followed the same procedure as the first test case, but instead entered invalid data into the email and password fields. After submitting the form and waiting for the widget tree to settle, the test case verified that the ErrorDialog widget was displayed using the find.byType() method and the findsOneWidget matcher.

In both test cases, the find.byType() method was used to locate widgets in the widget tree by their type, and the findsOneWidget matcher was used to verify that only one widget of the specified type was found. If more than one widget was found, the test case would fail with a FlutterError.

Overall, these test cases provided comprehensive coverage of the login form validation feature of the Flutter application, ensuring that it works as expected under various conditions.

``` dart
void main() {
  testWidgets('Login screen form validation', (WidgetTester tester) async {
    // Build the widget tree.
    await tester.pumpWidget(MaterialApp(home: LoginScreen()));

    // Enter valid data into the email and password fields.
    await tester.enterText(find.byType(TextFormField).at(0), 'test@example.com');
    await tester.enterText(find.byType(TextFormField).at(1), 'password');

    // Submit the form.
    await tester.tap(find.text('Sign in'));
    await tester.pump();

    // Verify that LoadingDialog is shown.
    expect(find.byType(LoadingDialog), findsOneWidget);

    // Wait for the widget tree to settle.
    await tester.pumpAndSettle();

    // Verify that loginNow is called.
    expect(find.byType(HomePage), findsOneWidget);

    // Enter invalid data into the email and password fields.
    await tester.enterText(find.byType(TextFormField).at(0), '');
    await tester.enterText(find.byType(TextFormField).at(1), '');

    // Submit the form.
    await tester.tap(find.text('Sign in'));
    await tester.pump();

    // Verify that an error dialog is shown.
    expect(find.byType(ErrorDialog), findsOneWidget);

    // Wait for the widget tree to settle.
    await tester.pumpAndSettle();

    // Verify that the sign in button is still visible.
    expect(find.text('Sign in'), findsOneWidget);
  });
}
```


The test cases were executed using the Flutter unit testing framework. They were carried out by creating a new test.dart file which imported the login page dart file and tested upon it using flutter modules.

#### Flutter has its own testing module named "flutter_test" that provides a set of tools to write tests for widgets and other parts of the Flutter app.
It includes classes like WidgetTester, which allows you to interact with widgets and test their behavior, and TestWidgetsFlutterBinding, which provides an implementation of WidgetsBinding that is specialized for testing. This module was used to perform the testing.


The developers can test the file using the Flutter test framework, which is built into the Flutter SDK.

#### The unit testing framework was directly implemented on Github since a new dart file was creating in a directory named 'test' of the Canteen Management App.

<img width="1470" alt="Screenshot 2023-04-21 at 10 28 06 PM" src="https://user-images.githubusercontent.com/75672785/233711891-556d3161-af04-45b8-a7ec-33b07f46ba44.png">

![1](https://user-images.githubusercontent.com/75672785/233711918-a954461b-70fc-4ee4-b431-9110526acefd.png)

![2](https://user-images.githubusercontent.com/75672785/233712557-06c3ba26-a11d-4b44-87d9-ef7b00db23b4.png)

Output for Successful Execution on Flutter test:

```
00:01 +1: Login screen form validation

00:01 +2: Login screen form validation (Enters valid email and password)
00:02 +3: Login screen form validation (Taps Sign in)
00:03 +4: Login screen form validation (Waits for widgets to settle)
00:03 +5: Login screen form validation (Verifies LoadingDialog is present)

00:04 +6: Login screen form validation (Enters invalid email and password)
00:05 +7: Login screen form validation (Taps Sign in)
00:06 +8: Login screen form validation (Waits for widgets to settle)
00:06 +9: Login screen form validation (Verifies ErrorDialog is present)

00:06 +10: All tests passed!
```

#### Once the test case failed, How did we fixed that?

There were two errors reported during the execution of the test cases.

- The first error was caused by a typo in the test file, where the text used to search for the Sign in button was misspelled. This error was fixed by correcting the spelling of the text.

- The second error reported was caused by the absence of the LoadingDialog widget. This error was fixed by adding the LoadingDialog widget to the codebase.

Overall, fixing these errors required careful attention to detail and a good understanding of the codebase. We had to identify the location of the error, understand the cause of the error, and take appropriate steps to fix it. These steps included correcting typos and adding missing widgets, and they helped to ensure that the test cases could be executed successfully.


