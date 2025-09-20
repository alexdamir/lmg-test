# Interview Questions and Answers

#### What is the difference between manual and automated testing?

  - Manual: humans execute tests; flexible but slow and error-prone. Automated: code runs tests; fast, repeatable, good for regression and scale.

#### Why do we use Python for automation?

  - Simple syntax, rich ecosystem (requests, Playwright/Selenium, pytest/behave), strong community, and easy CI/CD integration.

#### What are Python functions and why are they useful in automation?

  - Reusable blocks of code defined with def. They encapsulate steps, reduce duplication, and improve readability/maintainability.

#### What is a Python list?

  - An ordered, mutable collection: [1, "a", 3]. Supports indexing, slicing, and iteration.

#### What is a dictionary in Python?

  - A key–value mapping: {"user": "alice", "id": 1}. Fast lookups by key; ideal for structured test data. Duplicate keys are not allowed.

#### What is exception handling and how is it useful in tests?

  - try/except/finally to handle errors gracefully. Prevents hard crashes, allows cleanup, retries, and clearer failure messages.

#### How do you run a Python script from the terminal?

  - python path/to/script.py (use the virtualenv’s python).

#### What is PEP8?

  - Python’s official style guide for readable, consistent code (naming, formatting, imports, etc.).

#### What is Playwright?

  - A fast, reliable cross-browser automation library for Web (Chromium, Firefox, WebKit) with modern locator and auto-waiting.

#### How do you install Playwright in Python?

  - pip install playwright, then playwright install (or playwright install chromium/firefox/webkit). Poetry install.

#### How do you open a browser and navigate to a page in Playwright?

  - Launch browser, create page, goto URL. Example flow: launch → new_page → page.goto("https://...").

#### What is a selector in Playwright?

  - A query that identifies elements (XPATH, CSS, text, role, data-test). Prefer get_by_role/get_by_label for stability.

#### How do you click a button in Playwright?

  - Use a robust locator, e.g., page.get_by_role("button", name="Submit").click().

#### How do you fill a form field in Playwright?

  - page.get_by_label("Email").fill("user@example.com") or page.fill("css=selector", "value").

#### How do you wait for an element to appear in Playwright?

  - Implicit auto-wait via locators, or explicitly: locator.wait_for(state="visible") or page.wait_for_selector("selector", state="visible").

#### How do you handle multiple tabs or pages in Playwright?

  - Use the BrowserContext: await context.new_page(), or wait for "popup" events when links open new pages.

#### How do you take a screenshot in Playwright?

  - page.screenshot(path="page.png", full_page=True) or locator.screenshot(path="el.png").

#### What is BDD?

  - Behavior-Driven Development: describe behavior in business-readable language (Gherkin) to align stakeholders and guide tests.

#### What is Behave?

  - A Python BDD framework that executes Gherkin .feature files with step definitions in Python. (Cucumber for Python)

#### What is the structure of a .feature file?

  - Feature, optional Background, Scenario/Scenario Outline with Given/When/Then/And/But steps, and Examples for outlines.

#### What is a step definition in Behave?

  - A Python function bound to a Gherkin step via decorators (@given/@when/@then/@step) that implements the step’s logic.

#### Where are step definitions located in a Behave project?

  - In the steps/ directory (Python modules discovered by Behave).

#### How do you share data between steps in Behave?

  - Use the context object (context.var = value). It persists for the scenario (and can be scoped wider).

#### How do you run Behave tests from the command line?

  - behave (optionally with paths, -n 'Scenario name', --tags @tag, -D key=value).

#### What is the purpose of before_scenario in Behave?

  - A hook (in environment.py) to set up per-scenario state/resources (e.g., launch browser, seed data).

#### How do you use tags in Behave scenarios?

  - Add @tag above Feature/Scenario, then filter with --tags @tag (supports logical expressions like @a and not @b).

#### Can you integrate Playwright with Behave?

  - Yes. Initialize Playwright/browser in hooks (environment.py) and pass page/context via context to step implementations.

#### How would you explain your test framework to a non-technical manager?

  - It’s an automated safety net that simulates key user journeys, runs on every change, and reports clear pass/fail with evidence, reducing release risk and speeding delivery.

#### What would you automate first on a new web application?

  - Critical path smoke flows (login, signup, purchase), high-volume, stable, and business-critical scenarios.

#### When is it better not to automate a test?

  - One-off or rarely executed tests, rapidly changing UIs, highly subjective visual checks, or when automation cost outweighs value.

#### How do you debug a failed automation test?

  - Reproduce locally, run/debug headed/with slow-mo, collect logs/screenshots/videos/traces, check selectors and waits, isolate data/state, and minimize to the failing step.

#### What are flaky tests and how do you handle them?

  - Tests that pass/fail intermittently. Fix by stabilizing waits/selectors, removing sleeps, isolating state, mocking unstable dependencies, adding retries temporarily, and tracking flakiness.

#### How do you deal with dynamic elements in the UI?

  - Use resilient locators (role/label/data-test), explicit waits for state, avoid indexes, wait for network/idle, and prefer stable attributes over text that changes.

#### Why should you use the Page Object Model (POM)?

  - Encapsulation and reuse: separates page locators/actions from tests, improving readability, maintainability, and reducing duplication.

#### What tools can you use for test reporting?

  - Allure, built-in Behave/pytest reports, HTML reports, CI artifacts (screenshots/videos/traces), and dashboards in CI.

#### How do you validate data displayed in the UI?

  - Compare UI values to trusted sources (API/DB/fixtures), assert formats and totals, and verify with tolerances for time/currency when needed.

#### Why do you want to switch from manual testing to automation?

  - To scale coverage, speed feedback, reduce regressions, focus manual effort on exploratory testing, and grow technically.