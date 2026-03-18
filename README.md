# init-effect-subtree

Set up the [Effect-TS](https://github.com/Effect-TS/effect.git) source repo as a git subtree in your project, so AI coding agents can learn Effect patterns directly from source code.

This follows [Michael Arnaldi](https://x.com/MichaelArnaldi)'s (creator of Effect) recommended approach for training AI agents to write Effect code. Source code consistently outperforms docs, skills, and MCPs for LLM coding quality.

## Usage

Read the [SKILL.md](SKILL.md) and apply the approach with any AI coding agent.

Also installable as a skill:

```bash
npx skills add https://github.com/kevin-y-ang/init-effect-subtree
```

## In Michael's own words

> I had great success by adding the effect repo in a context folder as a subtree and let the llm explore it for patterns and solutions
>
> — [Michael Arnaldi, Sep 22 2025](https://x.com/MichaelArnaldi/status/1970091897575104761)

> I am having even better results by adding the effect repo as git subtree in a `.context/effect` folder, then telling AGENTS.md to look there for patterns
>
> — [Michael Arnaldi, Oct 7 2025](https://x.com/MichaelArnaldi/status/1975564356210598152)

> docs are very hard to get right I agree, in the meanwhile I am having a blast by adding the effect repo as a git subtree in my repositories and leverage claude to explain things and code
>
> — [Michael Arnaldi, Oct 11 2025](https://x.com/MichaelArnaldi/status/1977097736060379303)

> LLMs are fairly good at Effect if you add the effect repo in a .context dir as a git subtree, like exceptionally good.
>
> — [Michael Arnaldi, Oct 12 2025](https://x.com/MichaelArnaldi/status/1977431542159864024)

> Try adding the effect repo as a git subtree and let the ai explore it, it usually works exceptionally well
>
> — [Michael Arnaldi, Oct 16 2025](https://x.com/MichaelArnaldi/status/1978845657495425526)

> have you tried adding the effect repo as a git subtree in a context folder? I usually just tell claude to look there and come up with an impl, it can do absurdly complex stuff, e.g. today I had a session with @schickling where it implemented a fully working custom rpc transport
>
> — [Michael Arnaldi, Oct 26 2025](https://x.com/MichaelArnaldi/status/1982471154209026221)

> In my view LLM.txt and DOCS MCP should be both banned, the only thing that I found works reliably (with any lib, not only effect) is to add the library repo as a subtree in a .context directory, like .context/effect and then tell your local coding agent to look there for patterns, I've by now done it with widely different kinds of tasks and it always works exceptionally well, LLMs are great at searching in code and deriving understanding from it, consumes less context than LLM.txt and it's easier to use for the model than ad-hoc MCPs that the model ignores
>
> — [Michael Arnaldi, Oct 27 2025](https://x.com/MichaelArnaldi/status/1982725353878458405)

> Common misconception about AI coding: "Adding a repository as a subtree pollutes context". It's as incorrect as it can be, you're giving the AI the ability to search on demand whatever it needs when it needs it, MCPs pollute the context much more.
>
> — [Michael Arnaldi, Nov 12 2025](https://x.com/MichaelArnaldi/status/1988644856135389438)

> You miss that it doesn't materially improve the output, gets outperformed by simply adding effect as a git subtree in your repo
>
> — [Michael Arnaldi, Jan 28 2026](https://x.com/MichaelArnaldi/status/2016494096186056767)

> It's not the models it's how you use them, knowledge in models is always compressed, the best way is to add the effect repo as a subtree and index the patterns you use, add the subtree then tell the model "I want to use effect or effect/platform or effect/sql / etc please research the repo for best patterns and produce x-best-patterns.md"
>
> — [Michael Arnaldi, Jan 31 2026](https://x.com/MichaelArnaldi/status/2017856772795490510)

> Skills are terrible (benchmarked) clone the effect repo as a subtree and index it
>
> — [Michael Arnaldi, Jan 31 2026](https://x.com/MichaelArnaldi/status/2017855909112799416)

> We made and benchmarked one but it's underperforming using a local clone of the repo by a lot, my current intuition is that skills are not the right primitive to make AI good at X they are more to enable AI do repetitive things. LLMs are exceptional at understanding code
>
> — [Michael Arnaldi, Feb 28 2026](https://x.com/MichaelArnaldi/status/2027851074997260496?s=20)

> Of course like for everything AI is only an amplification engine of the knowledge of the user, so yes you still need to learn the patterns etc to use it well, lucky AI can also help there, the best way is to add the effect repo as a subtree of your own project and then ask AI questions, have AI generate best practices files, suggest patterns etc
>
> — [Michael Arnaldi, Feb 28 2026](https://x.com/MichaelArnaldi/status/2027839525964198024)

> GPT-5.4 is exceptional at Effect, just add the effect repo as a git subtree to give the agent access to best practices, skills don't work well.
>
> — [Michael Arnaldi, Mar 16 2026](https://x.com/MichaelArnaldi/status/2033640153672024162)

> Add the effect repository as a git subtree and ask the model to generate best practice files for what you want to use. Ignore skills they are useless for this purpose.
>
> — [Michael Arnaldi, Mar 17 2026](https://x.com/MichaelArnaldi/status/2033820438174851515)