**Prompt engineering in Copilot Chat**

In the previous section you discovered how to use basic prompts to get code from Copilot Chat. In this section you will learn techniques to get more accurate results using prompt engineering techniques.

**What is prompt engineering?** Prompt engineering is the process of designing high quality prompts to generate high quality code suggestions. There are good practices and tips to write better prompts. Let's see some of them.

**Provide examples: one-shot and few-shots programming**

Talking about prompt engineering, you can also use the chat to provide examples to Copilot. It's a good way to help Copilot understand what you want to do and generate better code. You can provide examples in the chat by typing with the validator.ts file open:

**one-shot programming**

> Write me unit tests for phone number validators methods using mocha and chai in the current file.

> Use the following examples for positive test (test that should return true):

```
it('should return true if the phone number is a valid international number', () => { expect(validatePhoneNumber('+33606060606')).to.be.true; });
```
> Organize test in logic suites and generate at least 4 positives tests and 2 negatives tests for each method.

**few-shot programming**

> Write me unit tests for all validators methods using mocha and chai in the current file.

> Use the following examples for positive test (test that should return true): 

> it('should return true if the phone number is a valid international number', () => { expect(validatePhoneNumber('+33606060606')).to.be.true; });

> it('should return true if the phone number is a valid local american number', () => { expect(validatePhoneNumber('202-939-9889')).to.be.true; });

> it('should throw an error if the given phone number is empty', () => { expect(validatePhoneNumber('')).to.throw(); });

> Organize test in logic suites and generate at least 4 positives tests and 2 negatives tests for each method.

You can use this technique to generate code that keeps the styling code from another file. For example if you want to create sample records for music style like the Albums in albums-api>Models>Album.cs file, open it and type:

> Write a MusicStyle record that conatins a List<MusicStyle> with 6 sample values like in the Album.cs file.

**Provide external references**

The chat copilot can use external references to build more accurate suggestions. For exemple if you want to generate a code that make a request to an API you can provide an example of the API response in the chat or the url to the API reference. Copilot will use it to generate better code.

> Write a TS function that retreiev all dog breeds from the following API and return an array of Breed objects Request: HTTP GET https://dog.ceo/api/breeds/list/all

Copilot will use the given external reference to generate the code. You will see that he wil generate the Breef interface (or class) with a subBreeds property. It's coming from the API given by the external reference.
```
interface Breed {
  name: string;
  subBreeds: string[];
}
```
You can also provide links to external documentations like SDK, libraries, etc... or event normative documents like RFCs, etc...

**Role Prompting**

Also called foundational prompt, it's a general prompt you're giving to Copilot Chat to personnalise his behavior and setup your flavour of Copilot.

This is probably the first thing to do when you start a new task with Copilot Chat: provide a clear description of what you want to build and how do you want copilot to help you.

> This is very powerfull when handled properly so be sure to start every coding sessions with a role prompt and save your best prompt for future use.

**Structure of a role prompt**

What can you include in a role prompt:

- Provide solid context and background information on what you want to build.
- Define GitHub Copilot’s role and setting expectations about what feedback we are looking for.
- Be specific in the quality of answers and ask for reference and additional resources to learn more and ensure the answers you receive are correct
- Resume the task and ask if the instructions are clear
  
**Example of a role prompt**

Start a new conversation and type the following prompt:

> I'm working on a new mobile application that is built on React Native.

> I need to build a new feature that will allow the user to upload a picture of a dog and get the breed of the dog.

> I will need to use the following set of APIs to work on the breeds: https://dog.ceo/api/breeds. I need to be sure that my code is secured againt at least the OWASP Top 10 treats (https://owasp.org/Top10/).

> I need to have unit tests for the code and i want my application to be fully accessible and conforms with the WCAG 2.1 level A and AA success criteria defined at https://www.w3.org/TR/WCAG21/.

> I need you to act as my own code coach to ensure that my code fits all these requirements.

> When possible, please provide links and references for additional learning.

> Do you understand these instructions? 

From there you can start asking questions and from time to time, ensure Copilot still follows the instructions by asking:

> Are you still using the instructions I provided?

**Test your role prompt**

You can test your role prompt by asking questions about best practices for accessibility on React Native Apps and OWASP Top 10 treats. You can also ask to generate code for the upload feature and check if the generated code is secured and accessible.

Try these questions for example:

> how can i make my app accessible with react native?

> what is the most secure way to upload a photo from my app?
