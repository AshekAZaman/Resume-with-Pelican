


# Resume with Pelican – README  

## Statement of Purpose  
This guide provides a step-by-step workflow for creating a professional resume website, inspired by Andrew Etter’s *Modern Technical Writing*. Using lightweight markup, static site generators, and version control, this method keeps your resume **easy to maintain**, **collaborative**, and **always up-to-date**. It streamlines showcasing your professional identity efficiently and accessibly.

**Why This Matters**:  
- **Lightweight Markup**: Writing in Markdown simplifies formatting, eliminating the need for Word or HTML. Its human-readable syntax lets you focus on content, making updates quick and easy, aligning with Etter’s advocacy for simplicity.  
- **Static Websites**: Pelican converts your resume into fast, secure HTML files, accessible anywhere, even offline. This improves user experience and security by removing server-side processing, unlike dynamic websites.  
- **GitHub Pages**: A free, version-controlled hosting solution that lets you update your resume by pushing changes. Following Etter’s “publish frequently” principle, it keeps your profile current with minimal effort.  


**Audience**:  
This guide is designed for professionals exploring modern documentation methods, including:  
- **New technical writers** eager to apply static site generators and version control to create structured, maintainable content.  
- **Non-developers** looking for a simple way to build and update a professional resume website without prior coding experience.  
- **Markdown learners** who want to expand their skills by using lightweight markup for clear, web-friendly formatting.
---

## Prerequisites  
Before building your resume, ensure you have these essential tools and skills:  

1. **Python 3.6+**  
   - Pelican, the static site generator, runs on Python, a widely used and reliable language.  
   - **Where to Get It**: Visit the [Python Installation Guide](https://www.python.org/) to download and set up Python.  

2. **Git**  
   - This version control system tracks file changes, supports collaboration, and allows reverting to previous versions.  
   - **Where to Get It**: Download Git from [Git SCM](https://git-scm.com/) and follow the installation steps.  

3. **GitHub Account**  
   - A GitHub account enables free hosting via GitHub Pages and simplifies version control and collaboration.  
   - **How to Start**: Sign up for a free account at [GitHub](https://github.com/).  

4. **Make (Windows Users)**  
   - Make automates repetitive build tasks like generating HTML files, ensuring consistency.  
   - **Installation**: Install Make via Chocolatey by running:  
     ```bash  
     choco install make  
     ```  

5. **Basic Markdown Knowledge**  
   - Markdown is a simple markup language used for structuring resume content.  
   - **Learn More**: Visit the [Markdown Syntax Guide](https://commonmark.org/help/) for a quick overview.
---

## Instructions  

### 1. Install Pelican with Markdown Support  
Andrew Etter advocates for lightweight markup to simplify workflows, and this step follows that principle.  

- **Action**: Install Pelican with Markdown support by running:  
  ```bash  
  python -m pip install "pelican[markdown]"  
  ```  
  This installs Pelican and the Markdown plugin, letting you write your resume in a clean, text-based format. By avoiding complex HTML or word processors, you can focus on content,aligning with Etter’s philosophy.

### 2. Set Up Make for Build Automation (Windows)  
Automation reduces manual effort and ensures consistency,key in modern technical writing.  

- **Action**: Install Make using Chocolatey:  
  ```bash  
  choco install make  
  ```  
  **Make** automates tasks like generating HTML files, ensuring a repeatable, error-free build process that saves time as you update your resume.

### 3. Initialize Your Pelican Project  
Pelican’s quickstart tool help setup the project.  

- **Action**: Run the configuration wizard:  
  ```bash  
  pelican-quickstart  
  ```  
  - **Title**: Enter "Resume with Pelican" or a custom title.  
  - **Author**: Input your full name (e.g., "Ashek A Zaman").  
  - **Time Zone**: Set your region (e.g., `America/Winnipeg`).  
  - Accept default settings unless customization is needed.  

This command generates essential project files, quickly preparing your resume website.

### 4. Write Your Resume in Markdown  
Markdown allows you to prioritize content over formatting, making it easier to focus on your words.  
- **Action**: Create a file named `home.md` in the `content/` folder with an introduction like this:  
  ```markdown  
  # Ashek A Zaman  
  *Software Developer*  
  Passionate about transforming complex ideas into clear, actionable insights.  
  ```  
- **Action**: Add detailed subsections, such as `education.md`, in the `content/pages/` directory:  
  ```markdown  
  # Education  
  **University of Manitoba** – BSc Computer Science (2018–2025)  
  - Relevant Courses: Data Structures and Algorithms, Data Structures, Technical Communication in Computer Science   
  ```  
You can further organize your resume by creating additional files (e.g., `experience.md` or `skills.md`), making it easier to update specific sections later.  

### 5. Apply a Pelican Theme for Readability  
A good theme boosts readability and professionalism, leaving a strong impression.  
- **Action**: Clone the Pelican themes repository:  
  ```bash  
  git clone --recursive https://github.com/getpelican/pelican-themes ~/pelican-themes  
  ```  
- **Action**: Set the "waterspill-en" theme in `pelicanconf.py`:  
  ```python  
  THEME = "~/pelican-themes/waterspill-en"  
  ```  
  Replace `~` with your home directory path (e.g., `C:/Users/YourName` on Windows). The "waterspill-en" theme is clean and professional, but feel free to explore other options.

### 6. Build and Preview Locally  
Testing your site locally before going live aligns with Etter’s advice to "test before publishing," helping you catch issues early.  
- **Action**: Build the site and launch a local server with this command:  
  ```bash  
  make html && make serve  
  ```  
  - Navigate to `http://localhost:8000` in your browser to see your resume as it will appear online. This step lets you review the layout, check for errors, and ensure everything looks polished before sharing it with the world.  

### 7. Deploy to GitHub Pages  
GitHub Pages provides a free, dependable hosting solution that’s perfect for static sites like your resume.  
- **Action**: Install `ghp-import`, a tool for deploying to GitHub Pages:  
  ```bash  
  python -m pip install ghp-import  
  ```  
- **Action**: Generate the production-ready version of your site:  
  ```bash  
  pelican content -s publishconf.py  
  ```  
- **Action**: Deploy it to GitHub with these commands:  
  ```bash  
  ghp-import output -b gh-pages  
  git push origin gh-pages  
  ```  
  Once deployed, your resume will be accessible at:  
  `https://yourusername.github.io/Resume-with-Pelican/`. This step not only makes your resume publicly available but also ties it to a platform that highlights your technical proficiency.  

---

## Troubleshooting  

### Issue 1: Theme Not Loading  
**Cause**: The `SITEURL` in your production settings might be incorrect, causing the theme to fail.  
**Fix**:  
1. Open `publishconf.py` and update the `SITEURL` to match your live site:  
   ```python  
   SITEURL = "https://yourusername.github.io/Resume-with-Pelican"  
   ```  
2. Rebuild and redeploy your site to apply the changes.  

### Issue 2: Changes Not Reflecting Post-Deployment  
**Cause**: This could stem from cached content or skipping a rebuild step.  
**Fix**:  
1. Rebuild the site to ensure all changes are included:  
   ```bash  
   make html  
   ```  
2. Redeploy to GitHub Pages:  
   ```bash  
   ghp-import output -b gh-pages  
   git push origin gh-pages  
   ```  
3. Clear your browser cache by performing a hard refresh (Ctrl + F5).  

### Issue 3: Markdown Formatting Errors  
**Cause**: Syntax errors, such as missing headers or incorrect indentation, can disrupt your layout.  
**Fix**:  
- Use a tool like the [Markdown Linter](https://github.com/markdownlint/markdownlint) to check your Markdown files for mistakes and ensure proper formatting.  

---

## Further Resources  
Here are some additional references to deepen your understanding and customize your project:  
1. **[Pelican Documentation](https://docs.getpelican.com/)**: Dive into advanced options for tweaking templates and adding plugins to enhance your site.  
2. **[GitHub Pages Guide](https://pages.github.com/)**: Learn how to set up a custom domain or troubleshoot hosting issues.  
3. **[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)**: A handy reference for mastering Markdown syntax quickly.  
4. **[Python Basics](https://docs.python.org/3/tutorial/)**: Brush up on Python skills to unlock more advanced Pelican customizations.  

---

## FAQs

### Q1: Why is Markdown better than raw HTML?   
**A**: Markdown’s simple, plain-text syntax eliminates the need for managing HTML tags, letting you focus on content.  
- **HTML**: `<h1>Education</h1><p><strong>University of Manitoba</strong> - BSc Computer Science</p>`  
- **Markdown**: `# Education\n**University of Manitoba** - BSc Computer Science`  
This simplicity aligns with Andrew Etter’s principle of reducing complexity in workflows, making your resume easier to create and maintain.

### Q2: My Markdown resume updates aren’t showing in the browser. What’s wrong?  
**A**: This issue can often be caused by:  
1. **Cached Content**: Clear the cache with Ctrl + F5 to see the latest version.  
2. **Missing Rebuild**: Run `make html` to regenerate your site.  
3. **Unpublished Changes**: Push your updates to GitHub Pages with:  
   ```bash  
   ghp-import output -b gh-pages  
   git push origin gh-pages  
   ```  
Following Etter’s advice to "publish frequently" ensures your live site reflects your most recent edits.  

### Q3: How can I collaborate on my resume?  
**A**: Use GitHub’s pull request feature for easy collaboration. Share your repository link, and others can:  
1. Fork the repo to make their own copy.  
2. Edit the Markdown files with suggestions or improvements.  
3. Submit a pull request for you to review and merge.  
This process follows Etter’s focus on distributed version control, enabling efficient teamwork while keeping the project organized.
---

## Credits  
- **Instructor** – Tristan Miller, for designing this assignment.  
- **Teaching Assistant** – Peter Vu, for providing assistance and guidance.  
- **Pelican** – The static site generator powering this resume-building approach.  
- **Waterspill-en Theme** – A contribution from the Pelican Themes Community for a polished look.  
- **Andrew Etter** – Inspiration drawn from his foundational principles in *Modern Technical Writing*.  
- **Peer Reviewers** – Nathan Parson and Shreshth Tyagi for their valuable feedback and insights.

