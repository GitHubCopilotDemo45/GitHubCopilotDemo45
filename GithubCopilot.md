This first challenges needs you to clone the following GitHub Repository: [Github Copilot Demo](https://github.com/Philess/gh-copilot-demo)

This repository is a code starter that will help you experiment all capabilities with GitHub Copilot. Take the time to look at the architecture design displayed on the page and when you're ready, clone the repository from the command line and open it in VS Code.

git clone https://github.com/Philess/gh-copilot-demo
cd gh-copilot-demo
code .

**Start playing with GitHub Copilot**
Once you start typing a prompt and copilot generate proposals, you can use the following shortcuts to interact with Copilot:

- tab to accept the current suggestion entirely (most common)
- ctrl + right arrow to accept word by word the suggestion (for partial use)
- alt + ^ to move to next suggestion
- shift + tab to go back to the previous suggestion
- ctrl+enter to display the copilot pane

**Natural Language Translations**
Automate text completion

Open file album-viewer/lang/translations.json

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

- Start adding a new block by adding a "," after the last "}" and press enter

**Code Generation**
**What is a prompt?** In the context of Copilot, a prompt is a piece of natural language description that is used to generate code suggestions. It's the input that Copilot uses to generate code. It can be a single line or a multiple lines description.

**Generate code from prompt**

Create a new album-viewer/utils/validators.ts file and start with the prompt:
// validate date from text input in french format and convert it to a date object

Copilot can help you also to write RegExp patterns. Try these:
// function that validates the format of a GUID string

// function that validates the format of a IPV6 address string

**Discover new tool and library on the job with Copilot**

Still on the same album-viewer/utils/validators.ts file add the following prompt:
// validate phone number from text input and extract the country code
For this one it will probably give you proposal that call some methods not defined here and needed to be defined. It's a good opportunity to explore the alternatives using the ctrl+enter shortcut to display the copilot pane.
You can choose one that uses something that looks like coming for an external library and use copilot to import it showing that the tool helps you discover new things.

**Complex algoritms generation**

In the albums-api/Controllers/AlbumController.cs file try to complete the GetByID method by replace the current return:
// GET api/<AlbumController>/5
[HttpGet("{id}")]
public IActionResult Get(int id)
{
    //here
}

In the same file you can show other prompts like:
// function that search album by name, artist or genre

// function that sort albums by name, artist or genre


