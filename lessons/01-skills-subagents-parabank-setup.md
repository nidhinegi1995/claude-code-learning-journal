# Claude Skills, Subagents & ParaBank Setup

**Claude Code Overview**

**Definition**

Claude Code is an AI coding agent that runs locally on your projects to assist with software development.

**Core Components**

1.  **Claude (LLM):** The underlying large language model.
2.  **Supporting Tools:** Surrounding software that enables access to project files, web searches, and terminal commands.
3.  **Modes of Operation:**
    -   **Planning Mode** – for structured project research.
    -   **Chat Mode** – for interactive Q&A.
    -   **Action Mode** – for text generation and tool execution.

**Three Key Concepts**

**1\. Claude Skills**

-   **Definition:** Reusable instructions stored as Markdown files (skill.md) that Claude can reference.
-   **Purpose:** Avoids re‑typing complex instructions into the context window for every task.
-   **Structure:**
    -   **Metadata:** Lightweight descriptors (name, description) to help Claude identify relevance.
    -   **Body:** Detailed instructions, templates, or standards.
-   **Comparison:**
    -   **Skills** = procedural knowledge.
    -   **MCP** = access to external tools/services.

**2\. Sub‑Agents**

-   **Purpose:** Manage context limits (200k tokens) by delegating tasks to specialized Claude instances.
-   **Mechanism:** The main agent decomposes complex requests and assigns them to sub‑agents, which return results.
-   **Built‑in Agents:**
    -   **Explorer:** Lightweight model for file discovery.
    -   **Planning:** Similar to the main agent, focused on codebase research.
    -   **General Purpose:** Full tool access for complex tasks.

**3\. System Under Test: ParaBank**

-   **Project:** ParaBank, a free open‑source banking web application, is used for demonstrations.
-   **Setup:**
    -   Clone the repository.
    -   Install requirements (Java JDK, Apache Maven, Apache Tomcat).
    -   Run locally and access via localhost:8080.

**🌐 What is Apache Maven?**

-   **Maven** is a **build automation and dependency management tool** for Java projects.
-   It helps you:
    -   **Compile** your code.
    -   **Run tests** automatically.
    -   **Package** your project into JAR/WAR files.
    -   **Manage dependencies** (e.g., if your project needs Spring or JUnit, Maven downloads the right versions for you).
    -   **Standardize project structure** using conventions (so every Maven project looks familiar).

Think of Maven as the "project manager" for Java—it keeps track of what your project needs and how to build it.

**📊 Quick Analogy**

-   **JDK** = toolbox (compiler, runtime).
-   **Maven** = project manager (knows which tools and materials you need, fetches them, and organizes the build).
-   **PATH/MAVEN\_HOME** = directions to where the toolbox/project manager lives.

**🌐 What is Apache Tomcat?**

-   **Tomcat** is an open-source **web server and servlet container**.
-   It runs Java web applications (like JSPs and Servlets) by interpreting Java code and serving it over HTTP.
-   Think of it as the “engine” that powers Java-based web apps, similar to how Node.js runs JavaScript apps.

**Start Tomcat**

-   Open **Command Prompt** and type:

Code

startup

-   Or double-click startup.bat inside the bin folder.

**Why?** → This launches Tomcat’s server process, which listens on port **8080** by default.

**Verify Installation**

-   Open a browser and go to:

Code

http://localhost:8080

-   You should see the Tomcat welcome page.

**Why?** → Confirms Tomcat is running and serving web content.

**🌐 What is a Port?**

-   A **port** is like a **doorway** into your computer that allows programs to communicate over the network.
-   Every computer has **65,536 ports** (numbered 0–65535).
-   When a program (like Tomcat, MySQL, or a browser) wants to send or receive data, it uses a specific port number.

**📊 Analogy**

Imagine your computer as a big office building:

-   The **IP address** is the building’s street address.
-   The **port number** is the specific room number inside the building.
-   If you want to deliver a package (data), you need both the building address (IP) and the room number (port).

**⚙️ Why Ports Matter in Tomcat**

-   By default, Tomcat listens on **port 8080**.
-   That means when you type:

Code

http://localhost:8080

your browser is knocking on “door 8080” of your computer, where Tomcat is waiting to serve web pages.

-   If another program is already using port 8080, Tomcat won’t start until you change its port in the server.xml configuration file.

👉 In short: mvn clean install **wipes old builds, compiles your project, runs tests, packages it, and installs the result into your local repository for reuse.**

mvn clean install **in Java projects is conceptually similar to installing dependencies in JavaScript with** npm install, but Maven does a bit more. Let’s compare:

Go to http://localhost:8080/parabank/

