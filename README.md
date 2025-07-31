# Awesome Claude Code Tips and Session Management

A comprehensive guide to effective Claude Code usage, covering session management, git workflows, and best practices for AI-assisted development.

## CLAUDE.md File

### Purpose
- Provides project-specific guidance to Claude Code
- Automatically read when starting a new session
- Maintains context between sessions

### What to Include
- Specific build commands (`npm run build:prod`) - see [npm documentation](https://docs.npmjs.com/cli/v7/commands/npm-run-script)
- Project architecture not obvious from file structure
- Custom workflows and conventions
- Important dependencies and tools

### What to Exclude
- Generic advice ("write clean code")
- Basic commands (`cd`, `ls`) - see [Unix command reference](https://ss64.com/bash/)
- Information obvious from reading files
- Temporary or experimental setups

### Keeping it Concise
- Use bullet points instead of paragraphs
- Group related information under clear headings
- Delete outdated information when adding new
- Test: "Will I need this next time I work on this project?"

## Session Lifecycle

### Start
- Reads CLAUDE.md from current project
- Loads global settings from `~/.claude/CLAUDE.md`
- Establishes fresh conversation context

### Active Session
- Maintains conversation memory
- Can read, write, and modify files
- Remembers previous exchanges in current chat
- Limited by [context window constraints](https://docs.anthropic.com/claude/docs/context-windows)

### End
- When exiting (Ctrl+C, closing terminal, timeout)
- Conversation memory is cleared
- Project files and CLAUDE.md remain intact

### After Session Ends
- **Persists:** Repository files, CLAUDE.md, package.json, configs
- **Cleared:** Conversation history, in-memory context
- **Next session:** Starts fresh with file-based context

## Context Persistence

### How Context Syncs
1. **CLAUDE.md file** - Primary method, stays in repository
2. **Repository files** - Source code, package.json, configs
3. **Global CLAUDE.md** - Personal preferences at `~/.claude/CLAUDE.md`

### Updating CLAUDE.md
- Ask during conversation: "update CLAUDE.md"
- Include new commands, architecture decisions, project setup
- Best practice: update before ending session
- Focus on project-specific information

## Best Practices

### During Development
- Update CLAUDE.md when establishing new commands
- Add architecture decisions as they're made
- Include project-specific conventions

### Before Ending Session
- Ask to summarize and save context to CLAUDE.md
- Remove outdated information
- Ensure all essential commands are documented

### Evaluation Criteria
- **Include if:** Specific commands, unique architecture, custom workflows
- **Exclude if:** Generic advice, basic commands, obvious information
- **Test:** Would you understand the project reading this cold?

## Example CLAUDE.md Structure

```markdown
# CLAUDE.md

## Project Overview
Brief description of project purpose and tech stack

## Essential Commands
- Build: `npm run build` (outputs to dist/) - see [npm scripts](https://docs.npmjs.com/cli/v7/using-npm/scripts)
- Test: `npm test` (runs Jest with coverage) - see [Jest documentation](https://jestjs.io/docs/getting-started)
- Dev: `npm run dev` (starts on port 3000)

## Architecture Notes
- Uses [Redux Toolkit](https://redux-toolkit.js.org/introduction/getting-started) for state management
- API layer in src/services/ with [axios](https://axios-http.com/docs/intro) interceptors
- Components follow [container/presenter pattern](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)

## Git Workflow
- Create feature branches before implementing new functionality - see [Git branching](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
```

## Tips for Effective Use

1. **Keep it short** - 10-30 lines is ideal
2. **Be specific** - Include actual commands you use
3. **Stay current** - Remove outdated information
4. **Focus on uniqueness** - What makes this project different?
5. **Update regularly** - Add context as the project evolves

## Anti-Intuitive Tips

### Less is More
- **Counter-intuitive:** Shorter CLAUDE.md files are more effective than comprehensive ones
- **Why:** I'll read your actual source code anyway - CLAUDE.md should just point me to the unique/important parts
- **Action:** Delete obvious information. If I can figure it out from reading package.json or src/, remove it.

### Don't Document Everything
- **Counter-intuitive:** Only document what you'd forget or what's not obvious
- **Why:** Your future self (and I) can read code. We need help with the "why" and "how", not the "what"
- **Action:** Focus on decisions, conventions, and non-standard setups.

### Outdated Information is Worse Than No Information
- **Counter-intuitive:** It's better to have minimal CLAUDE.md than an outdated one
- **Why:** Wrong information leads to wrong actions. No information leads to investigation
- **Action:** Aggressively remove anything that's no longer accurate.

### I Don't Need Your Personal Preferences
- **Counter-intuitive:** Don't include your coding style preferences
- **Why:** I'll adapt to your existing code style automatically
- **Action:** Remove "I prefer camelCase" or "use async/await instead of promises"

### Conversation History is Temporary - Files are Permanent
- **Counter-intuitive:** Our conversation doesn't matter as much as what we write to files
- **Why:** Next session starts fresh, but files remain
- **Action:** Make sure important context gets written to CLAUDE.md or actual code files.

### Don't "Save for Later"
- **Counter-intuitive:** Don't wait until the end of session to update CLAUDE.md
- **Why:** You might forget important context or end the session unexpectedly
- **Action:** Update it immediately when you establish something important.

### Specificity Over Generality
- **Counter-intuitive:** "Run `npm run build:staging --verbose`" is better than "Build the project"
- **Why:** Vague guidance forces me to guess or investigate
- **Action:** Include the exact commands you actually use.

### The "Would I Need This?" Test
- **Counter-intuitive:** Ask yourself this question for every line in CLAUDE.md
- **Why:** If the answer is "I could figure this out from reading the code," remove it
- **Action:** Be ruthless about keeping only what's truly valuable.

## Session Management

### Ideal Session Length
- **Short sessions (15-30 minutes):** Single file changes, quick questions, small refactoring
- **Medium sessions (30 min - 2 hours):** Building features, multiple file changes, setup tasks
- **Long sessions (2+ hours):** Large-scale refactoring, deep architectural changes
- **Sweet spot:** 1-2 hours for focused development work

### When to End a Session
- Task is naturally complete
- Starting a new, unrelated task
- Context is getting cluttered with unrelated topics
- You've achieved your main goal

### Task Scope for One Session
**Good scope:**
- Build one complete feature (auth, API endpoint, UI component)
- Fix one specific bug with its root cause
- Refactor one module or service
- Set up one piece of infrastructure
- Write one comprehensive test suite - see [testing best practices](https://testing-library.com/docs/)

**Characteristics:**
- Achievable in 1-2 hours
- Has clear completion criteria
- Stays cohesive (all parts relate)
- Creates value at completion

### Multiple Sessions
**No simultaneous sessions** - Only one Claude Code session per project at a time
**What you CAN do:**
- Multiple terminals with different projects
- Sequential sessions in same project
- Different Claude instances (web + CLI)

**Best practice:** One session per project at a time, use CLAUDE.md for context persistence

## Git & GitHub Workflows

### Git Philosophy
**You control git operations, I help with quality:**
- **You handle:** Branch creation, commits, pushes, merges
- **I help with:** Commit messages, PR descriptions, git commands
- **Why:** Git operations are permanent decisions in your project
- **Learn more:** [Pro Git Book](https://git-scm.com/book/en/v2)

### Feature Branch Workflow
```bash
# You: Create feature branch
git checkout -b feature/name

# Me: Work on code changes
# You: Review and commit
git diff
git commit -m "feat: descriptive message" # See [Conventional Commits](https://www.conventionalcommits.org/)

# Me: Draft PR description
# You: Create PR
gh pr create --title "title" --body "description" # See [GitHub CLI](https://cli.github.com/manual/gh_pr_create)
```

### Commit Message Best Practice
- **I write:** High-quality commit messages following conventions
- **You review:** Check the message and changes before committing
- **Result:** Better git history with your final control

### Pull Request Process
- **I draft:** PR descriptions with checklists and test plans
- **You create:** Actual PR with my suggested content
- **I help:** Respond to reviews, suggest improvements
- **You decide:** When to merge and integrate

### GitHub Integration
**What I can help with:**
- Drafting PR descriptions and checklists
- Writing [GitHub Actions](https://docs.github.com/en/actions) workflows
- Creating [issue templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-issue-forms)
- Analyzing PR changes for potential issues

**What you control:**
- PR creation and merging
- Issue creation and assignment
- Team workflow decisions
- Repository permissions

### Complete Workflow Example
See [example-workflow.md](example-workflow.md) for a complete end-to-end example of adding a feature from branch creation to PR merge.

## Anti-Patterns to Avoid

### Git Anti-Patterns
- ❌ Working on main branch
- ❌ Giant commits with unrelated changes
- ❌ Committing broken code "to save it"
- ❌ Not reviewing what I've changed
- ❌ Abandoned feature branches

### Session Anti-Patterns
- ❌ Sessions that are too long (>4 hours)
- ❌ Trying to do too many unrelated tasks
- ❌ Not updating CLAUDE.md before ending
- ❌ Scope creep during sessions

### CLAUDE.md Anti-Patterns
- ❌ Including personal coding preferences
- ❌ Generic advice and best practices
- ❌ Outdated or incorrect information
- ❌ Documentation that duplicates obvious file structure

## Advanced Tips

### Communication Strategies

**Be Specific and Concrete**
- **Instead of:** "Fix the bug"
- **Say:** "The login form shows 'Invalid credentials' even with correct password. Check auth service in src/auth.js"
- **Learn more:** [How to ask good questions](https://stackoverflow.com/help/how-to-ask)

**Provide Context Early**
- **Share:** "I'm using React with Redux, the API is in src/services/, and I follow functional components"
- **Why:** I can give better answers when I understand your stack
- **Reference:** [React documentation](https://react.dev/)

**Use Examples**
- **Show me:** What you want the output to look like
- **Share:** Error messages, expected behavior, current behavior

**Break Down Complex Requests**
- **Instead of:** "Build the whole admin panel"
- **Say:** "First, let's create the user list component with search and pagination"

### Task Management

**Use the TodoWrite Tool**
- **For:** Complex tasks with multiple steps
- **When:** Any task requiring 3+ distinct actions
- **Benefit:** Visual progress tracking for both of us

**Start Small, Iterate**
- **First:** Get the basic functionality working
- **Then:** Add error handling, validation, styling
- **Finally:** Optimize and add advanced features

**Prioritize by Value**
- **Focus:** What delivers the most value first
- **Ask:** "What's the minimum viable version of this feature?"
- **Build:** Core functionality before edge cases

### Error Handling

**Share Complete Error Messages**
- **Copy:** Full error stack traces, not just "it doesn't work"
- **Include:** Error location, line numbers, relevant code context
- **Why:** I can pinpoint issues faster with complete information

**Debug Systematically**
1. **Reproduce:** Confirm the issue consistently
2. **Isolate:** Find the minimal case that triggers it
3. **Investigate:** Check related code and dependencies
4. **Fix:** Address root cause, not just symptoms

**Common Error Patterns**
- **Import issues:** Check file paths and exports - see [ES modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
- **Async problems:** Look for missing await/then - see [async/await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- **State issues:** Check component lifecycle and state updates
- **API errors:** Verify endpoints, headers, and data formats

### Performance Optimization

**Session Performance**
- **Be concise:** Shorter prompts get faster responses
- **Batch requests:** Ask for multiple things at once
- **Use context:** Reference previous work instead of repeating

**Code Performance**
- **Ask specifically:** "Optimize this database query" vs "Make it faster"
- **Profile first:** "This function is slow, can you help optimize it?"
- **Measure:** Include performance metrics if available

### Learning and Growth

**Learn from My Explanations**
- **Ask why:** "Why did you choose this approach?"
- **Request alternatives:** "What are other ways to solve this?"
- **Understand trade-offs:** "What are the pros and cons of this solution?"

**Build Your Knowledge**
- **Take notes:** Save patterns and techniques you learn
- **Apply concepts:** Use similar approaches in future work
- **Teach others:** Explaining concepts reinforces learning

### Testing Strategies

**Test-Driven Development**
- **Start with tests:** Define what success looks like first
- **Write failing tests:** Confirm the test catches the issue
- **Implement:** Make the test pass
- **Refactor:** Clean up the implementation

**Testing Patterns to Include**
- **Happy path:** Expected successful scenarios
- **Edge cases:** Empty inputs, null values, boundary conditions
- **Error handling:** Invalid inputs, network failures
- **Integration:** How components work together
- **Resources:** [Testing Pyramid](https://martinfowler.com/articles/practical-test-pyramid.html)

### Code Review Best Practices

**Review My Changes**
- **Always check:** `git diff` before committing
- **Look for:** Security issues, performance problems, bugs
- **Question:** Anything that doesn't make sense
- **Suggest:** Improvements based on your project standards

**Give Good Feedback**
- **Be specific:** "Line 42 has a potential null reference" vs "This has bugs"
- **Explain why:** "This approach might cause memory leaks because..."
- **Suggest solutions:** "Consider using useMemo here instead"

### Project Setup Tips

**New Project Checklist**
- [ ] Initialize version control - see [Git init](https://git-scm.com/docs/git-init)
- [ ] Set up basic project structure
- [ ] Configure build tools
- [ ] Set up testing framework
- [ ] Create CLAUDE.md with initial setup
- [ ] Set up [CI/CD pipeline](https://docs.github.com/en/actions/getting-started-with-github-actions/about-github-actions)
- [ ] Add documentation structure

**Environment Management**
- **Use .env files:** For configuration and secrets - see [.env best practices](https://create-react-app.dev/docs/adding-custom-environment-variables/)
- **Document setup:** Include environment setup instructions
- **Version control:** Exclude sensitive files with [.gitignore](https://git-scm.com/docs/gitignore)

### Documentation Beyond CLAUDE.md

**README.md Structure**
- Project purpose and features
- Installation and setup instructions
- Usage examples
- API documentation (if applicable)
- Contributing guidelines
- License information

**Code Comments**
- **Explain why:** Not just what the code does
- **Document decisions:** Why this approach was chosen
- **Mark TODOs:** For future improvements or known issues
- **Reference:** [Code comment best practices](https://www.thoughtfulcode.com/comment-your-code/)

### Collaboration Tips

**Working with Teams**
- **Communicate:** Let team know you're using AI assistance
- **Review:** All AI-generated code before committing
- **Document:** AI usage in commit messages if required by team
- **Quality:** Maintain the same code quality standards

**Knowledge Sharing**
- **Share what works:** Effective patterns and workflows
- **Document lessons:** What worked and what didn't
- **Help others:** Teach team members effective AI collaboration

### Tool Integration

**Useful Combinations**
- **Claude + Git:** Better commit messages and PR descriptions
- **Claude + Testing:** Write comprehensive test suites
- **Claude + Documentation:** Generate clear documentation
- **Claude + Code Review:** Get second opinions on changes
- **Reference:** [AI-assisted development best practices](https://www.anthropic.com/claude-code)

**Automation Opportunities**
- **GitHub Actions:** I can write CI/CD workflows - see [GitHub Actions docs](https://docs.github.com/en/actions)
- **Scripts:** Automate repetitive development tasks
- **Templates:** Generate code templates for common patterns

### Mindset and Approach

**Treat Me as a Tool**
- **You're in charge:** Make final decisions
- **I'm an assistant:** Provide options and expertise
- **Collaborate:** Work together rather than delegating

**Quality Over Speed**
- **Take time:** Review my work before committing
- **Iterate:** Improve solutions through feedback
- **Standards:** Maintain your project's quality bar

**Continuous Improvement**
- **Update CLAUDE.md:** As your project evolves
- **Refine workflows:** Based on what works best
- **Learn patterns:** Both from me and from experience