# Resume with Pelican – README

## Statement of Purpose

This README provides a step-by-step guide to creating and hosting a resume website using modern technical writing tools, as inspired by Andrew Etter’s *Modern Technical Writing*. It is intended for individuals with basic technical skills, some familiarity with Markdown, and an interest in learning about static site generators and version control. The process involves writing a resume in Markdown, generating a static site with Pelican, and deploying it to GitHub Pages, all while aligning with Etter’s principles of lightweight markup, static site generators, distributed version control, and forges.


## Prerequisites

Before following these instructions, ensure you have:

- **Python** installed on your system. (Installation instructions: [Install Python](https://www.python.org/))
- A basic understanding of the command line.
- **Git** installed for version control. (Download: [Git SCM](https://git-scm.com/))
- A GitHub account and the GitHub Desktop app (Download: [GitHub Desktop](https://desktop.github.com/download/)).
- **Make** installed (on Windows, via Chocolatey: [Make Installation](https://stackoverflow.com/q/32127524)).
- Familiarity with **Markdown**. (Tutorial: [Markdown Tutorial](https://www.markdowntutorial.com/))

## Instructions

Follow these steps to create and host your resume website.

### 1. Install Pelican with Markdown support

- Open a command prompt and run:

    `python -m pip install "pelican[markdown]"`

- This installs Pelican along with Markdown support.

### 2. Install Make (Windows users)

- Install Chocolatey from [chocolatey.org](chocolatey.org), then run this in an administrator command prompt:

  `choco install make`

### 3. Create a new Pelican project

- Run:

    `pelican-quickstart`

- Answer the prompts as follows:
  - Where to create the website: . (current directory)
  - Title: "Resume with Pelican"
  - Author: Your name (e.g., "Ashek A Zaman")
  - Default language: en
  - URL prefix: n
  - Article pagination: Y (default)
  - Articles per page: 10
  - Time zone: Your time zone (e.g., America/Winnipeg)
  - Generate tasks.py/Makefile: Y
  - Upload options: N for all

- This sets up the project structure.

### 4. Write your resume in Markdown

- Create a file named home.md in the content directory. Example content:

  `# Ashek A Zaman`

  `A brief introduction about myself.`

- Add separate pages for sections like Education, Experience, Skills, and Projects in content/pages/. For example, education.md:

  `# Education`
  
  `**University Name** - Degree, Years`

### 5. Apply a theme to your site

- Clone the Pelican themes repository:  
  
  `git clone --recursive https://github.com/getpelican/pelican-themes ~/pelican-themes`

- I chose the "waterspill-en" theme (demo: pelicanthemes.com/waterspill-en).

- Edit pelicanconf.py and set:

    `THEME = "/path/to/~/pelican-themes/waterspill-en"`

- Replace `/path/to/` with the actual path to the theme directory

### 6.Build and preview your site locally

- This generates the site in the `output` directory.
- Run:

    `make serve`

- Visit `http://localhost:8000` in your browser to preview the site.

### 7. Set up a GitHub repository
- Create a new repository on GitHub (e.g., "Resume-with-Pelican").
- Use GitHub Desktop or the command line to clone it locally and commit your project files.

### 8 Deploy your site to GitHub Pages.

- Install ghp-import:

    `python -m pip install ghp-import`

- Generate the site for production:

    `pelican content -s publishconf.py`

- Import the output to the gh-pages branch:

    `ghp-import output -b gh-pages`

- Push to GitHub:

`git push origin gh-pages`

- Your site will be live at `https://yourusername.github.io/Resume-with-Pelican/`.

### 9 Troubleshoot theme issues

- If the theme doesn’t load, edit `publishconf.py` and set:

SITEURL = "https://yourusername.github.io/Resume-with-Pelican"

- Rebuild and redeploy the site (repeat step 8’s commands).

## Further Resources

For additional reading and to deepen your understanding, please refer to:

- [Python Official Site](https://www.python.org/) – For downloading and learning about Python.
- [Python Tutorial](https://docs.python.org/3/tutorial/index.html) – Official Python documentation.
- [Pelican Themes on GitHub](https://github.com/getpelican/pelican-themes) – Explore different themes for Pelican.
- [Markdown Tutorial](https://www.markdowntutorial.com/) – An interactive guide to Markdown.
- [GitHub Pages Documentation](https://pages.github.com/) – Learn more about hosting static sites on GitHub.

## FAQ

**Q: Why is Markdown better than writing raw HTML for documentation?**  
**A:** Markdown is designed for simplicity. It allows you to focus on content rather than complex syntax, making the documentation more readable and easier to maintain. This approach is consistent with Etter’s principle of clarity.

**Q: I updated my Markdown resume, but the changes aren’t visible on the live website. What should I do?**  
**A:** After modifying your Markdown files, you must regenerate the site using `make html` (or the appropriate Pelican command) and then redeploy the site using `ghp-import` and `git push`. Also, ensure to clear your browser cache or perform a hard refresh.

## Credits

- **Ashek A Zaman** – Author and primary contributor.
- **Pelican** – Open-source static site generator used for this project.
- **Waterspill-en Theme** – Theme provided by the Pelican Themes community ([Pelican Themes GitHub](https://github.com/getpelican/pelican-themes)).
- **GitHub Pages** – Used as the hosting forge.
- Special thanks to the contributors of Andrew Etter’s *Modern Technical Writing* for the guiding principles applied throughout this project.
