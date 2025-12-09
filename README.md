# code-editor-rules
# AI Code Editor Rules & Best Practices

**Accelerate development with battle-tested settings for Cursor, Windsurf, VSCode & Antigravity—no advanced coding knowledge required.**

Perfect for teams, beginners, and anyone who wants consistent, high-quality code without memorizing best practices.

***

## 📋 Table of Contents

- [Why These Rules Exist](#why-these-rules-exist)
- [Quick Start](#quick-start)
- [Core Development Rules](#core-development-rules)
- [Tool-Specific Setup](#tool-specific-setup)
- [For Non-Coders: What This All Means](#for-non-coders-what-this-all-means)

***

## 🎯 Why These Rules Exist

These rules act as a **safety net and quality control system** that catches problems before they reach production. Think of them as spell-check, grammar-check, and a writing coach combined—but for code. They ensure that:

- **Nothing gets forgotten** (checklists, documentation, tests)
- **Mistakes can be undone** (rollback plans, changelogs)
- **Everyone follows the same playbook** (consistent patterns, clear naming)
- **Security isn't an afterthought** (secrets handling, configuration)
- **The code actually works** (testing requirements, validation steps)

***

## ⚡ Quick Start

1. **Copy the rules** from the sections below based on your editor
2. **Paste into your project** following the tool-specific instructions
3. **Start coding**—the rules will guide you automatically

***

## 🔧 Core Development Rules

### 1. Plan Before You Build

**The Rule:** Before writing any code, create a mini design + test plan. List all assumptions and questions with three possible options for each, including rationales. Wait for approval before proceeding.

**Why it matters:** This prevents building the wrong thing. It's like drawing blueprints before constructing a house—much cheaper to erase a line on paper than rebuild a wall. It forces you to think through edge cases and gets everyone aligned upfront.

**Who benefits:** 
- **Beginners:** Get guidance on what to consider before coding
- **Teams:** Avoid miscommunication and wasted effort
- **Managers:** See what's being built and why

***

### 2. Always Document Changes

**The Rule:** Every code change must update `CHANGELOG.md` with version number, timestamp, and *why* architectural decisions were made.

**Why it matters:** When something breaks six months later, you'll know exactly what changed and why. It's a flight recorder for your project that helps you understand the reasoning behind decisions, not just what changed.

**Who benefits:**
- **Future you:** Remember why you made that weird choice
- **New team members:** Understand project history quickly
- **Debugging:** Trace when bugs were introduced

***

### 3. Have an Escape Plan

**The Rule:** Every release must include rollback notes, especially for database changes. Include both forward-fix and rollback paths.

**Why it matters:** Sometimes deployments fail or cause unexpected problems. A rollback plan is your "undo button" for production. Without it, you're stuck with broken software while scrambling for a fix.

**Who benefits:**
- **Everyone:** Sleep better knowing you can undo mistakes
- **Users:** Experience less downtime when things go wrong
- **Business:** Protects revenue and reputation

***

### 4. Handle Unreliable Tests

**The Rule:** Flaky tests (tests that sometimes pass, sometimes fail) must be tagged with "quarantine" and a dated follow-up task. Quarantined tests still run separately and are reported.

**Why it matters:** Unreliable tests train you to ignore test failures. When everything is red, you miss real problems. Quarantining separates "actually broken" from "unreliable" while ensuring issues get fixed.

**Who benefits:**
- **Developers:** Trust your test suite again
- **Code quality:** Real bugs don't get lost in noise
- **Velocity:** Stop wasting time on false alarms

***

### 5. Keep Visibility into Your System

**The Rule:** Maintain structured logs with correlation IDs and error taxonomies. Include log checks in validation steps.

**Why it matters:** When users report "it's broken," logs tell you what actually happened. Without them, you're guessing. Structured logs are like having a security camera on your code—everything is recorded and searchable.

**Who benefits:**
- **Support teams:** Diagnose user issues quickly
- **Developers:** Debug faster with clear trails
- **Business:** Understand system health and usage patterns

***

### 6. Never Hardcode Secrets

**The Rule:** Never commit secrets (passwords, API keys). Use `.env` files locally and a secrets manager in production. Document config changes in tests and docs.

**Why it matters:** Secrets in code get stolen by hackers scanning GitHub. One mistake can cost your company millions in breaches. This rule is like always locking your front door—basic security hygiene.

**Who benefits:**
- **Security:** Protect user data and company assets
- **Compliance:** Meet legal requirements (GDPR, SOC2)
- **Peace of mind:** No emergency "we leaked all our keys" incidents

***

### 7. Use Absolute Paths

**The Rule:** All file references must use absolute paths (like `/Users/yourname/project/file.js`), never relative paths (`../../file.js`).

**Why it matters:** Relative paths break when you move files or run code from different locations. Absolute paths always work, eliminating mysterious "file not found" errors that waste hours of debugging.

**Who benefits:**
- **Stability:** Code works reliably across environments
- **Refactoring:** Move files without breaking imports
- **Onboarding:** New developers don't get stuck on path issues

***

### 8. Keep Architecture Documentation Current

**The Rule:** Any architectural change must update both `ARCHITECTURE_DIAGRAM.mmd` (Mermaid diagram) and `ARCHITECTURE_DOCUMENTATION.md` in the same release.

**Why it matters:** Outdated documentation is worse than no documentation—it actively misleads. Keeping diagrams and docs in sync means anyone can understand your system by viewing one file. The single large diagram ensures you see the whole system, not fragmented pieces.

**Who benefits:**
- **New hires:** Understand the system quickly
- **Stakeholders:** See how pieces fit together
- **Maintenance:** Know where to make changes safely

***

### 9. Standardize Branch Names & Pull Requests

**The Rule:** Use prefixes `feat/`, `fix/`, `chore/` for branch names. Every PR must link to a release number and include a checklist (tests updated, docs updated, changelog updated).

**Why it matters:** Consistent naming makes automation possible and helps everyone understand what a change does at a glance. Checklists prevent human error—like forgetting to update docs after a feature change.

**Who benefits:**
- **Automation:** Tools can parse branch names for releases
- **Reviewers:** Quickly understand change intent
- **Quality:** Nothing important gets forgotten

***

### 10. Test Everything, Every Time

**The Rule:** Run `testing/run_all_test_scripts.sh` after every change. Record results in `cursor_log.md`. Maintain coverage gates to catch regressions immediately.

**Why it matters:** Tests catch bugs before users do. Running them constantly means you find problems when they're small and fresh in your mind. It's like having spell-check run automatically instead of manually once a week.

**Who benefits:**
- **Confidence:** Ship code knowing it works
- **Speed:** Catch bugs earlier when they're cheaper to fix
- **Sleep:** Fewer production emergencies

***

### 11. Give AI Clear Problem Statements

**The Rule:** Every request to AI must include: context, symptoms/logs, desired outcome, and validation steps. This keeps prompts actionable and reduces rework.

**Why it matters:** AI is powerful but not psychic. Vague requests produce vague results. Clear problem statements are like giving a contractor detailed blueprints versus saying "build something nice"—the results are dramatically better.

**Who benefits:**
- **Efficiency:** Get correct solutions faster
- **Accuracy:** AI understands what you actually need
- **Documentation:** Requests become debugging paper trails

***

### 12. Maintain a Living Changelog for AI

**The Rule:** The changelog file isn't just for humans—it's for the AI to reference before making changes, ensuring it learns from past decisions and maintains consistency.

**Why it matters:** AI doesn't have memory between sessions. The changelog acts as its long-term memory, preventing it from repeating mistakes or reintroducing old bugs. It's like giving the AI a project diary to read before starting work.

**Who benefits:**
- **Consistency:** AI maintains project conventions
- **Learning:** AI improves from past changes
- **Quality:** Avoids regressing to old patterns

***

### 13. Generate Production-Ready Code

**The Rule:** When generating code, always consider: error handling, edge cases, performance optimization, and scalability. Include clear comments explaining the logic and follow best practices for the language/framework.

**Why it matters:** Code that works in happy scenarios breaks in production when real users encounter edge cases. This rule ensures your code is robust, fast, and maintainable—not just functional.

**Who benefits:**
- **Users:** Experience stable, fast software
- **Maintenance:** Code is easier to understand and modify
- **Scale:** Software grows without performance collapse

***

### 14. Systematic QA & Bug Fixing

**The Rule:** When asked for a QA report, act as QA: report all failed services and functions. Then act as engineering: patch all issues. Run all tests, deploy to cloud, and test the entire backend end-to-end.

**Why it matters:** Separating QA and engineering mindsets ensures thorough testing before fixing. End-to-end testing after patching verifies fixes don't break other things. It's like having a professional inspector check your work before calling the job done.

**Who benefits:**
- **Quality:** Bugs get fixed completely, not partially
- **Confidence:** Comprehensive testing prevents shipping new bugs
- **Professionalism:** Deliver polished, working software

***

### 15. Diagnose Before Treating

**The Rule:** When encountering bugs, reflect on 5-7 possible sources. Distill to 1-2 most likely causes. Add logs to validate assumptions before implementing fixes. Fix causes, not symptoms.

**Why it matters:** Treating symptoms masks problems temporarily; fixing causes solves them permanently. Adding logs first ensures you understand the problem instead of guessing. It's like a doctor running tests before surgery instead of just prescribing painkillers.

**Who benefits:**
- **Quality:** Fixes solve real problems
- **Efficiency:** Avoid wasting time on wrong solutions
- **Learning:** Understand your system deeply

***

## 🛠️ Tool-Specific Setup

### Cursor IDE

**Where to put these rules:**
- **Global rules:** Cursor Settings → Rules (applies to all projects)
- **Project rules:** Create `.cursor/rules/` directory in your project, add `.mdc` files
- **Legacy method:** Root-level `.cursorrules` file (still works but deprecated)

**Why this structure:** Global rules are your personal preferences. Project rules are team standards that travel with the code. Keeping rules in version control means new team members automatically get the right guidance.

***

### Windsurf Editor

**Where to put these rules:**
- **Global rules:** File → Preferences → Windsurf Settings → Global Rules
- **Workspace rules:** `.windsurf/rules/` directory with `.md` files
- **File limit:** Keep each rule file under 6,000 characters for Cascade to read it properly

**Why this structure:** Similar to Cursor, but Windsurf uses a "rules directory" approach. The character limit ensures the AI can process your rules efficiently without performance issues.

***

### VSCode

**Where to put these rules:**
- **Workspace settings:** `.vscode/settings.json` in your project
- **Comments:** Add comments in `settings.json` to explain configurations
- **Extensions:** Install recommended extensions via `.vscode/extensions.json`

**Why this structure:** Workspace settings ensure everyone on the team uses the same configuration. Comments help teammates understand why certain settings exist. This is especially important for remote teams.

***

### Antigravity IDE

**Where to put these rules:**
- **Global rules:** Settings → Customizations → + Global Rule
- **Workspace rules:** Settings → Customizations → + Workspace Rule
- **Workflows:** Define sequences of actions the agent should follow
- **Artifacts:** Rules can reference `task.md`, `implementation_plan.md`, `walkthrough.md`

**Why this structure:** Antigravity is agentic—it operates in a Plan → Execute → Verify loop. Rules define how it plans and verifies. Workflows automate repetitive tasks like generating tests or documentation.

***

## 👶 For Non-Coders: What This All Means

If you're new to coding or working with developers, here's the simple version:

**These rules are guardrails that:**
- **Prevent mistakes** before they happen (planning requirements, checklists)
- **Make problems easy to fix** (rollback plans, good logs, documentation)
- **Keep everyone aligned** (consistent patterns, clear naming, current diagrams)
- **Ensure quality** (testing requirements, QA processes, security rules)
- **Save time** (catching bugs early is 10x cheaper than fixing them later)

**You don't need to memorize these.** Just copy them into your project and let them guide you. The rules will remind you what to do, catch oversights, and help you produce professional-quality software—even if you're just starting out.

***

## 🤝 Contributing

These rules evolve with real-world experience. If you have suggestions:

1. Fork the repository
2. Add your rule with clear "why" explanation
3. Submit a pull request with the checklist below

### PR Checklist

- [ ] Rule includes clear "why" explanation for non-coders
- [ ] Rule includes "who benefits" section
- [ ] Documentation updated (`ARCHITECTURE_DOCUMENTATION.md`)
- [ ] Changelog updated with version and reasoning
- [ ] Tests added/updated
- [ ] Rollback plan included (if applicable)

***

## 📄 License

MIT License - feel free to use these rules in personal and commercial projects.

***

**Pro Tip:** Start with just 2-3 rules that address your biggest pain points. Add more as your team grows. The goal is better software, not more bureaucracy.
