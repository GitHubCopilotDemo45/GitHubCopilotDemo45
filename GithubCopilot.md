This first exercise needs you to clone the following GitHub Repository: [Github Copilot Demo](https://github.com/Philess/gh-copilot-demo)

This repository is a code starter that will help you experiment all capabilities with GitHub Copilot. 
```
git clone https://github.com/Philess/gh-copilot-demo

cd gh-copilot-demo

code .

```

**Start playing with GitHub Copilot**
Once you start typing a prompt and copilot generate proposals, you can use the following shortcuts to interact with Copilot:

- tab to accept the current suggestion entirely (most common)
- ctrl + right arrow to accept word by word the suggestion (for partial use)
- alt + ^ to move to next suggestion
- shift + tab to go back to the previous suggestion
- ctrl+enter to display the copilot pane

**Natural Language Translations**

**Automate text completion**

Open file album-viewer/lang/translations.json

```
[
    {
        "language": "en",
        "values": {
            "main-title": "Welcome to the world of the future",
            "main-subtitle": "The future is now with copilot",
            "main-button": "Get started"
        }
    }
]
```

- Start adding a new block by adding a "," after the last "}" and press enter

**Code Generation**

**What is a prompt?** In the context of Copilot, a prompt is a piece of natural language description that is used to generate code suggestions. It's the input that Copilot uses to generate code. It can be a single line or a multiple lines description.

**Generate code from prompt**

Create a new album-viewer/utils/validators.ts file and start with the prompt:

> // validate date from text input in french format and convert it to a date object

Copilot can help you also to write RegExp patterns. Try these:

> // function that validates the format of a GUID string

> // function that validates the format of a IPV6 address string

**Discover new tool and library on the job with Copilot**

Still on the same album-viewer/utils/validators.ts file add the following prompt:

> // validate phone number from text input and extract the country code

> For this one it will probably give you proposal that call some methods not defined here and needed to be defined. It's a good opportunity to explore the alternatives using the ctrl+enter shortcut to display the > copilot pane.
> You can choose one that uses something that looks like coming for an external library and use copilot to import it showing that the tool helps you discover new things.

**Complex algoritms generation**

In the albums-api/Controllers/AlbumController.cs file try to complete the GetByID method by replace the current return:
```
// GET api/<AlbumController>/5
[HttpGet("{id}")]
public IActionResult Get(int id)
{
    //here
}
```

In the same file you can show other prompts like:

> // function that search album by name, artist or genre

> // function that sort albums by name, artist or genre

**Big tasks vs small tasks**

**Big Prompts and Short Prompts**

Copilot will probably will always more effective with prompt to generate small but precisely described pieces of code rather than a whole class with a unique multiple lines prompt.

> The best strategy to generate big piece of code, is starting by the basic shell of your code with a simple prompt and then adding small pieces one by one.

**Big prompts that could works**

- Back in the albums-viewer/utils add a new file viz.ts to create a function that generates a graphe. Here is a sample of prompt to do that:
  
> // generate a plot with d3js of the selling price of the album by year

> // x-axis are the month series and y-axis show the numbers of album selled

> // data from the sales of album are loaded in from an external source and are in json format

> Copilot will probably try to complete the prompt by adding more details. You can try to add more details yourself or follow copilot's suggestions. When you want it to stop and start generating the code just jump on another line and let the copilot do its work.

- Once you achieved to generate the code for the chart you probably see that your IDE warn you about the d3 object that is unknown. For that also Copilot helps. Return on top of the file and start typing import d3 to let copilot autocomplete
```  
import d3 from "d3";
```

Look at what Copilot has been able to generate. It's possible that the code is working fine and does everything you asked for but also you probably hit the token limit and Copilot was not able to generate the whole code.

It's because Copilot for autocompletion is not made for creating big pieces of code at once, but is more specialized in generating small pieces step by step.

**Try again by build it step by step**

Try to generate the code for the plot by cutting it into small pieces following the steps below:
```
import * as d3 from 'd3';
```
> // load the data from a json file and create the d3 svg in the then function

Inside the then function, starts by setting up the basics of the plot

> // create the svg

> // create the scales for the x and y axis

> // x-axis are the month series and y-axis show the numbers of album selled

> // create axes for the x and y axis

From there you can just ask to copilot to complete the chart

> // generate a line chart based on the albums sales data

You will always get better results by cutting big task into small chunks with copilot autocomplete. It's also a good way to show that copilot is not magic and you have to use it with your other IDE feature and your developer logic.

**Tests**
Copilot can help generate all kind of tests that are written with code. It Includes unit tests, integration tests, end to end tests, and load testing tests with jmeters scripts for example.

- Add a new file validators.test.ts in the albums-viewer/tests folder

- To have good test suggestion, you hould provide some basic informations to Copilot such as the test framework you want to use:
```
import { describe }
```

When you start typing the describe function, copilot will see you're in test file in TS and suggest you to import the describe and it functions from Mochai which is a famous test framework for JS/TS. Accept the suggestion and it will automatically suggest also the expect function from Chai: accept it also.
```
import {describe, it} from 'mocha';
import {expect} from 'chai';
```

You have your test framework in place! Now just import the functions you want to test by starting a new line by import keyword copilot will see you are in a test file, to test some validators because of the name and it will suggest something like that:
```
import {validateAlbumId} from '../src/validators';
```

It looks ok but because Copilot doesn't have access to all your code, only the open tab and limited informations, you can see that both the path and the function name are wrong.
... At least he tried ...
but it's a good way to show that Copilot is not magic and you have to use it with your other IDE feature and your brain :)

- Accept the suggestion and change the path. You will be able to have VS Code to give you the available function with the ctrl+space shortcut.

- Add a comment with the first function you want to test and let the magic happen:
```
import {describe, it} from 'mocha';
import {expect} from 'chai';

import {validateDate, validateIPV6} from '../utils/validators';

// test the validataDate function
```
Boom!
```
describe('validateDate', () => {
    it('should return a date object when given a valid date string', () => {
        const date = '01/01/2019';
        const expectedDate = new Date(2019, 0, 1);
        expect(validateDate(date)).to.deep.equal(expectedDate);
    });

    it('should throw an error when given an invalid date string', () => {
        const date = '01/01/2019';
        expect(() => validateDate(date)).to.throw();
    });
});
```
You can add other it block to add more test cases and also add the tests for the other functions. For example try add a new it block for the validateDate function to test that it throws and error when given en empty string.

**Writing documentation**

Copilot can understand a natural language prompt and generate code and because it's just language to it, it can also understand code and explain it in natural language to help you document your code. So it can help you in all your documentation tasks. It can generate simple documentation comment or standardized documentation comment like JavaDoc, JsDoc, etc... it can also help you translate your documentation in different languages. Let's see how it works.

**simple documentation comment**
To see that just put you pointer on top of a Class, a method or any line of code and start typing the comment handler for the selected language to trigger copilot. In language like Java, C# or TS for example, just type //and let the magic happen.

Here is an example in the albums-viewer/routes/index.js file. Insert a line and start typing on line 13 inside the try block
```
router.get("/", async function (req, res, next) {
  try {
    // Invoke the album-api via Dapr
    const url = `http://127.0.0.1:${DaprHttpPort}/v1.0/invoke/${AlbumService}/method/albums`;
```
Continue to play with it and see what happens on other pieces of code.

**standardized documentation comment (JavaDoc, JsDoc, etc...)**
For this one, to trigger the documentation comment generation, you need to respect the specific comment format:

- /** (for JS/TS) in the index.js file for example
- /// for C# in the AlbumController.cs of the AlbumApi file for example
  
```
/// <summary>
/// function that returns a single album by id
/// </summary>
/// <param name="id"></param>
/// <returns></returns>
[HttpGet("{id}")]
public IActionResult Get(int id)
```
**Writing markdown and html documentation**

Copilot is also very powerfull to help you write documentation. It can generate markdown and html code and accelerate the writing of your readme.md files like for this one for example.

You can show that by creating a new file demo.md in the root of the project and start typing the following prompt:

> # Github Copilot documentation
> This documentation is generated with Github Copilot to show what the tool can do.

> ##

From there by starting a new line with a secondary level title it will start generating the content of the documentation and it will showcase how it will accelerate the documentation writing process.
