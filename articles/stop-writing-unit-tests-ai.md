# Stop Writing Unit Tests by Hand: Automate it with AI

Let's face it: no developer enjoys writing unit tests. We all know test-driven development (TDD) and high code coverage are best practices, but when you are under a tight deadline to ship a feature, writing exhaustive Jest or Mocha tests for edge cases feels like a chore.

Because of this, codebases inevitably accumulate technical debt. Tests are skipped, coverage drops, and bugs creep into production.

## The Problem with AI Code Generators

With the rise of ChatGPT and GitHub Copilot, many developers tried to solve this by pasting their code into a prompt and asking, "Write tests for this."

While this works for simple functions, it completely breaks down for complex files with multiple dependencies. More importantly, it forces you to constantly copy and paste code between your IDE and a browser, breaking your flow state.

## Enter `ai-test-gen`

To solve this friction, the open-source community created **[ai-test-gen](https://github.com/albertstayhome/ai-test-gen)**. 

`ai-test-gen` is a blazing-fast, zero-dependency CLI tool that lives directly in your terminal. It uses the Gemini API to analyze your local source files and automatically generate complete, production-ready unit test files using standard frameworks (like Jest, Mocha, or Vitest).

### Why it's a Game Changer:

1. **Zero Configuration:** There are no complex config files to set up. It just works out of the box.
2. **Zero Installation:** Because it uses Node's native fetch API, it has zero dependencies. Run it anywhere via `npx`.
3. **Context-Aware:** It reads the entire file, imports the correct functions, and mocks dependencies intelligently.

### See it in action

To generate tests for a file, simply export your API key (which you can get for free from Google AI Studio) and run the command against your target file:

```bash
export GEMINI_API_KEY="your_api_key_here"
npx github:albertstayhome/ai-test-gen src/utils/formatter.js
```

Within seconds, a new file `src/utils/formatter.test.js` will appear in your directory.

```javascript
import { formatCurrency, formatDate } from './formatter';

describe('Formatter Utilities', () => {
  describe('formatCurrency', () => {
    it('should format USD correctly', () => {
      expect(formatCurrency(1000, 'USD')).toBe('$1,000.00');
    });
    it('should handle zero values gracefully', () => {
      expect(formatCurrency(0, 'USD')).toBe('$0.00');
    });
    // ... extensive edge cases generated automatically
  });
});
```

You just saved 20 minutes of tedious typing. Run your test suite, verify the output, and move on to the next feature.

## Reclaim Your Engineering Hours

By adopting `ai-test-gen`, you can enforce 100% test coverage policies without slowing down your feature delivery. 

For more zero-dependency tools that automate modern development workflows (including context packing for LLMs, i18n translation, and bash generation), check out the **[Awesome AI Developer Workflow](https://github.com/albertstayhome/awesome-ai-dev-workflow)** repository. 

Stop writing boilerplate tests. Let the AI handle the coverage while you handle the logic.
