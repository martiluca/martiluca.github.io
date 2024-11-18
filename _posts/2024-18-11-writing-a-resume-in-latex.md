---

layout: distill

title: Writing a Resume with LaTeX

date: 2024-18-11

description:  Creating a resume that stands out can be a challenge. Here, I present you a guide on how to use my template to create a good looking resume in LaTeX and I share some of the tips and tricks that I learned along the way.

tags: resume cv template stem latex

categories: LaTeX

featured: true

authors:

​    - name: Martina Lucà

---

<div class=“alert alert-warning”>
 	<div class="title">
        <span>Important</span>
        <span><i class="fa-regular fa-message"></i></span>
    </div>
	 <p>
    	This post will refer to my template (<a href="https://github.com/martiluca/cvitae">cvitae</a>). 
    </p>
</div>

## Introduction

Creating a resume that stands out can be a challenge, but it's essential. Whether you're applying for an internship or a graduate program, a well-structured resume can set you apart from the competition. My LaTeX template, cvitae, is designed with STEM students in mind. With customizable colors, a modern font, and dedicated sections for research and academic experiences, this template makes it easy to create a polished resume tailored to your needs. Plus, the power of LaTeX guarantees consistent formatting and professional-quality output every time.

Ready to dive in? Let’s explore how you can use this template to create a resume that truly reflects your expertise and potential.

### Features

The **cvitae** template is designed to be minimal and eye catching at the same time. Here’s what makes it stand out:

- **Customizable colors for a personal touch**  
  The template supports the Open Color palette, allowing you to select a main color. Whether you prefer a professional navy blue or a vibrant teal, the choice is yours.  

- **Dedicated sections for essential information**  
  Each section is designed to highlight the key aspects of your resume:  
  - **Education**: Showcase your academic achievements.  
  - **Research Experience**: Detail your projects and contributions to science.  
  - **Work Experience**: Highlight internships or relevant jobs.  
  - **Skills**: Share your technical proficiencies.  
  - **Certificates**: List any certifications or training.  
  - **Publications**: Feature your published works or conference presentations.  

- **Presentation box**  
  The template includes a self-adjusting presentation box with rounded corners, perfect for displaying your name, contact details, and a profile picture.   

- **Modern design elements**  
  - **Hyperlinks**: directly link your email, LinkedIn, GitHub, or other profiles for easy access.  
  - **FontAwesome Icons**: add recognizable icons.  
  - **Raleway Font**: a clean and modern font to ensure your resume looks contemporary and professional.  

## Step 1: set up your environment and download the template

To start using the **cvitae** template, you’ll need a working LaTeX setup. Depending on your preferences, you can either work locally on your computer or use an online LaTeX editor like Overleaf. 

### Option 1: clone and compile locally

Start by downloading and installing a LaTeX distribution. This is the engine that processes the .tex files and generates a PDF. The distribution you need depends on your operating system. You can find a guide for Windows, Linux and MacOS [here](https://www.tug.org/texlive/).

Next, choose a LaTeX editor. This is the program you’ll use to write and edit your resume. Two great options are:

- TeXstudio, a user-friendly editor with a simple interface.
- VS Code paired with the LaTeX Workshop extension. I personally use this option. If you want to set this up on MacOS, I suggest [this](https://www.youtube.com/watch?v=CmagZthwhaY) tutorial by Federico Tartarini.

Once your tools are installed, it’s time to download the cvitae template. You can find it on Github in [this repo](https://github.com/martiluca/cvitae). From here, you can either download the file as .zip 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/cvitae-get.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>    

or, if you are familiar with git, you can clone the repository directly with the `git clone` command:

```bash
git clone https://github.com/martiluca/cvitae.git

```

Open the .tex file in your chosen editor. From there, use the `Compile` or `Build` function to generate a PDF. In most editors, this will be as simple as clicking a button or pressing a shortcut key. If everything is set up correctly, you should be able to generate your PDF within seconds.

### Option 2: use Overleaf

For those who prefer not to install anything locally, Overleaf is a good alternative. This is a cloud-based LaTeX editor that lets you edit and compile LaTeX documents directly in your browser. 

To get started, create a free account at [Overleaf](https://www.overleaf.com/). Once logged in, download the **cvitae** template as a .zip from GitHub. In Overleaf, click `New Project`, then select `Upload Project`. Drag and drop the .zip file, or use the file picker to upload it.


<div class="alert alert-tip">
    <div class="title">
        <span>Tip</span>
        <span><i class="fa-regular fa-lightbulb"></i></span>
    </div>
  <p>
    If you're new to LaTeX, Overleaf is a beginner-friendly option. It eliminates the need for local installations and simplifies the entire process.  
  </p>
  <p>
    However, keep in mind that Overleaf's free version has limitations, including reduced compilation time. Moreover, they further reduced compilation time; my personal opinion is that they are trying to push users to get one of the paid plans. For this reason, I recommend starting with Overleaf if you're a beginner and transitioning to local compilation as soon as you feel confident enough.
  </p>
</div>

## Step 2: customize your resume

### Profile box

The profile box at the top of the resume is designed to present your contact information, profile picture, and a brief summary about yourself. It’s generated using the following command in the main.tex file:

```latex
\introduction{\name\ \surname}{profile.pdf}{\address}{\phone}{\email}{\birthday}{\website}{\whoami}
```

Before this command, you’ll find a series of definitions where you can insert your personal information. Simply update the values like `\name`, `\surname`, `\email`, and others to reflect your details.

The only part you need to modify directly inside the `\introduction` command is the path to your profile picture. Replace profile.pdf with the path to your desired image file. 

### Change the main color

The main color is defined in the .cls file. To set a new one, add the following command before the the `\introduction` command:

```latex
\renewcommand{\maincolor}{oc-red-7}
```

This command sets the main color to oc-red-7 from the [Open color palette](https://yeun.github.io/open-color/). You can choose from a range of colors available in the palette, such as oc-blue-6, oc-green-5, or any of the other predefined color names.


### Fill in the details in each section

Each section of the template is pre-built to accommodate specific types of information, but you can easily modify them or create new ones based on your needs. Below is an example of how to structure and fill in a section, such as Education:

```latex
\cvsect{Education}

\begin{entrylist}
    \entry
        {Start Date -- End Date}
        {Degree \\ Field of Study}
        {Institution}
        {Description of your studies, thesis, and any relevant details.}
    % Add more entries as needed
\end{entrylist}
```

You can find more detailed examples within the template itself, so refer to them to get a better understanding of how to format other sections such as Research Experience, Work Experience, Skills, and Publications. Each section includes multiple examples to help guide you as you customize your resume.

<div class="alert alert-tip">
    <div class="title">
        <span>Tip</span>
        <span><i class="fa-regular fa-lightbulb"></i></span>
    </div>
  <p>
    Keep your content concise. A clean, uncluttered resume is easier to read and leaves a stronger impression. Avoid overly long descriptions and focus on quantifiable achievements whenever possible. 
  </p>
  </p>
</div>

## Conclusion
Here’s a draft for the **Conclusion** section that ties everything together:

Your revision sounds great! It's personal and engaging while keeping the tone professional. Here's a slightly refined version with just a couple of small tweaks for flow:

## Conclusion

Creating a resume that stands out can be difficult, and I hope this template has made the process more straightforward for you.

I encourage you to explore and customize the template to reflect your unique qualifications. If you have any suggestion for improvement or new feature ideas, feel free to [open an issue on GitHub](https://github.com/martiluca/cvitae) or contact me via [email](mailto:martina.luca@univr.it).

I hope this guide has been helpful. See you next time!
