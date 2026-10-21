# prompt-engineer

A simple skill that takes care of your prompts. It writes a new one or improves yours, then tries to break it and fixes the weak spots before you use it.

You describe the task in your own words, even in one line. Claude asks a few short questions about the rules it cannot guess, then writes the prompt to the current prompting guidance for the model that will run it.

It does not stop at a well-written draft: it attacks it. It reads the draft the way the model, a careless user and someone trying to misuse it would, looks for where it fails, and fixes what it finds.

You get the prompt, ready to copy, and a short answer: does it do the job, what the attack found, and what the prompt cannot handle on its own, such as a permission, a check in your code or a model setting.

It writes prompts for Claude and other models: system prompts, agents, Claude Projects, Custom GPTs, Gemini Gems, CLAUDE.md files and skills.

## Use

Ask for a prompt the way you would ask a colleague:

```text
I need a system prompt for a support bot that can look up orders.
Make this prompt shorter and safer: <paste the prompt, or attach the file>
```

Claude starts the skill on its own when you ask for a prompt. In Claude Code you can also call it with `/prompt-engineer:refine-prompt <request>`. Answer the questions, say "ok" to take the defaults it proposes, or say "proceed" to skip them.

## What it runs

The plugin is one skill: a single file of instructions for Claude. It has no scripts, hooks, connectors or subagents, so it sends no data anywhere beyond your conversation with Claude. Claude reads a file only when you give it one, and writes no file unless you ask for one.

## More

The [repository](https://github.com/HighMarck17/prompt-engineer) has the full README, with a real example from the request to the finished prompt.

License: MIT.
