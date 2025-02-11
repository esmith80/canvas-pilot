---
name: "Intro to Programming"
uuid: 739714f8-59d0-49b8-bbc3-31e2e7e4ffe4
duration: 20
questions:

  -
    question: "What does `console.log(...)` do in the Node.js environment?"
    uuid: d895e755-2e5f-4ba1-a463-1f3a2bbd245a
    outcome: 5f66ee62-ea91-4697-917e-4abb014554d9
    options_attributes:
      -
        answer: "Logs a string to a file on local disk"
        explanation: "Incorrect, interacting with the filesystem would require the `fs` module"
      -
        answer: "Prints the given argument to the standard output, or terminal"
        explanation: "Correct, it outputs to the stream known as STDOUT"
        correct: true
      -
        answer: "Keeps the parameters in memory for later use"
        explanation: "Incorrect, the console.log does not store anything in memory"
      -
        answer: "Ignores it unless it's configured to do something"
        explanation: "Incorrect, by default the console.log prints a statement somewhere"

  -
    question: "What is the difference to fork and clone a code repository?"
    uuid: 07510f25-88a6-40ad-874f-c433d8870bb7
    outcome: b5e212af-a45d-4104-926a-b8c413718e43
    options_attributes:
      -
        answer: "Fork copies the repository on the server, and clone copies it to the local disk"
        explanation: "Correct, fork is an action used on GitHub to copy a repo to your account"
        correct: true
      -
        answer: "Fork copies the repository to your local disk, and clone copies it remotely"
        explanation: "Incorrect, forking a repo doesn't copy it to your local disk"
      -
        answer: "There is no difference, they both duplicate the repo on the server"
        explanation: "Incorrect, cloning does not duplicate the repo on the server"
      -
        answer: "There is no difference, they both copy the repo to the local disk"
        explanation: "Incorrect, forking doesn't copy the repo to your local disk"

  -
    question: |
      What will be logged to the console?

      ```javascript
      var globalScope = 'I\'m all up in your codes!';

      if (true) {
        let globalScope = 'Not anymore, you\'re not!';
      }
      console.log(globalScope);
      ```

    uuid: e6275ab0-6455-48f0-9b0f-2a17a75e235b
    outcome: dd93d5ef-8d98-4861-b4f6-de5995365374
    options_attributes:
      -
        answer: "I'm all up in your codes!"
        explanation: "Correct! The `let` declaration is scoped to it's containing block, which means that our `console.log()` ignores it completely."
        correct: true
      -
        answer: "Where mah codes at?!"
        explanation: "You know this is wrong. Don't be silly."
      -
        answer: "Not anymore, you're not!"
        explanation: "The `let` declaration is scoped to it's containing block. This definition is not accessible outside of that block."

  -
    question: |
      What will be logged to the console?

      ```javascript
      x = 12;
      if(true) {
        x + 2;
        x = 4;
      }
      console.log(x);
      ```

    uuid: 9f08b164-fd4d-40d5-826d-e646d1d53eb0
    outcome: dd93d5ef-8d98-4861-b4f6-de5995365374
    options_attributes:
      -
        answer: "6"
        explanation: "Even though we are adding 2 to `x`, we aren't returning that value, and then we immediately overwrite the value of `x` on the next line."
      -
        answer: "12"
        explanation: "Because we have no `let` or `var` declaration, the value of `x` is scoped globally, and is overwritten inside of the conditional statement."
      -
        answer: "4"
        explanation: "Correct! `x` is set as a global variable, and is not contained inside any function or block scope. It is overwritten inside the conditional statement, and retains it's new value when the block closes."
        correct: true

  -
    question: |
      What will the following code output to the console?

      ```javascript
      console.log(friend);
      var friend = 'E.T.';
      console.log(friend);
      ```

    uuid: 80c11e2c-5675-49b0-8e8a-4989dcc4b871
    outcome: 15b1aee2-a15f-48e0-bc7c-ad92b2d61dd6
    options_attributes:
      -
        answer: |
          ```bash
          ReferenceError: friend is not defined
          ```
        explanation: "The declaration of `friend` will be hoisted to the top, before the first `console.log` – `friend` will therefore already be defined."
      -
        answer: |
          ```bash
          undefined
          E.T.
          ```
        explanation: "`friend` is hoisted to the top but given no value, therefore the first `console.log` will say `undefined`. Then, the value `\"E.T.\"` is set to `friend` before the second `console.log` which will output `\"E.T.\"`. "
        correct: true
      -
        answer: |
          ```bash
          friend
          E.T.
          ```
        explanation: "`friend` is a variable, and `console.log(friend)` will output the variable's value not the variable's name. When a variable is declared but not assigned a value, its value will be `undefined`."
---
