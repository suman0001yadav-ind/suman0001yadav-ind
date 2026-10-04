<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Suman Kumar Yadav - Portfolio Banner</title>
    
    <!-- Google Fonts for standard text (Poppins) and handwritten text (Caveat) -->
    <link href="https://fonts.googleapis.com/css2?family=Caveat:wght@600&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <!-- FontAwesome for the role icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Devicon for original colored Tech Stack icons -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css">

    <style>
        :root {
            /* The specific bright blue used in the image */
            --brand-blue: #1DA1F2; 
            --text-light: #E1E8ED;
        }

        body {
            margin: 0;
            padding: 0;
            background-color: #0b111a;
            font-family: 'Poppins', sans-serif;
            color: #ffffff;
        }

        /* Banner Container */
        .banner-container {
            position: relative;
            width: 100%;
            background-color: #0c121e; /* Fallback color */
            background-size: cover;
            background-position: center;
            height: 450px;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        /* Animated Dark gradient overlay */
        .banner-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(-45deg, rgba(4,10,18,0.9), rgba(4,10,18,0.4), rgba(29, 161, 242, 0.1), rgba(4,10,18,0.9));
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            z-index: 1;
        }

        .content {
            position: relative;
            z-index: 2;
            text-align: center;
            width: 100%;
            max-width: 1400px;
        }

        /* Floating Handwritten Text */
        .handwritten {
            position: absolute;
            font-family: 'Caveat', cursive;
            font-size: 26px;
            color: #d1d9e6;
            line-height: 1.1;
            letter-spacing: 1px;
            z-index: 2;
            /* Animation applied here */
            animation: float 4s ease-in-out infinite;
        }

        .handwritten.left {
            left: 80px;
            top: 60px;
            /* Using a CSS variable so the animation retains the tilt */
            --rot: -10deg; 
            transform: rotate(var(--rot));
            text-align: left;
        }

        .handwritten.left .blue-code {
            color: var(--brand-blue);
            font-family: 'Poppins', monospace;
            font-weight: 700;
            font-size: 24px;
            display: block;
            margin-top: 5px;
        }

        .handwritten.right {
            right: 80px;
            top: 60px;
            --rot: -8deg;
            transform: rotate(var(--rot));
            text-align: right;
            animation-delay: 1.5s; /* Delays right text float for a staggered effect */
        }
        
        .handwritten.right::after {
            content: "";
            display: block;
            width: 80%;
            height: 2px;
            background: #d1d9e6;
            margin-top: 5px;
            margin-left: auto;
            border-radius: 2px;
        }

        /* Main Heading */
        h1 {
            font-size: 58px;
            font-weight: 700;
            letter-spacing: 2px;
            margin: 0 0 15px 0;
            text-transform: uppercase;
            text-shadow: 0 2px 10px rgba(0,0,0,0.5);
            /* Slide up fade-in */
            opacity: 0;
            animation: slideUpFade 1s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
        }

        h1 .blue-text {
            color: var(--brand-blue);
            display: inline-block;
            animation: textGlow 3s ease-in-out infinite alternate;
        }

        /* Roles / Titles */
        .roles {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            font-size: 15px;
            font-weight: 300;
            margin-bottom: 25px;
            opacity: 0;
            animation: slideUpFade 1s cubic-bezier(0.2, 0.8, 0.2, 1) 0.3s forwards;
        }

        .roles i {
            color: var(--brand-blue);
            margin-right: 6px;
        }

        .roles .separator {
            color: #445566;
            font-weight: 300;
        }

        /* Tagline */
        .tagline {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            font-size: 18px;
            color: var(--text-light);
            margin-bottom: 35px;
            opacity: 0;
            animation: slideUpFade 1s cubic-bezier(0.2, 0.8, 0.2, 1) 0.5s forwards;
        }

        .horizontal-line {
            height: 1px;
            width: 60px;
            background-color: #2c4c70;
        }

        /* Tech Stack Border Container */
        .tech-stack-box {
            border: 1px solid rgba(29, 161, 242, 0.4);
            border-radius: 25px;
            padding: 20px 40px;
            display: inline-block;
            margin-bottom: 30px;
            background: rgba(4, 10, 18, 0.3);
            backdrop-filter: blur(5px);
            opacity: 0;
            animation: slideUpFade 1s cubic-bezier(0.2, 0.8, 0.2, 1) 0.7s forwards;
            transition: box-shadow 0.4s ease, border-color 0.4s ease;
        }

        .tech-stack-box:hover {
            box-shadow: 0 0 20px rgba(29, 161, 242, 0.2);
            border-color: rgba(29, 161, 242, 0.8);
        }

        .tech-stack-box legend {
            color: var(--brand-blue);
            font-size: 13px;
            letter-spacing: 3px;
            text-transform: uppercase;
            padding: 0 15px;
            font-weight: 600;
        }

        /* Tech Stack Icons */
        .tech-icons {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 30px;
        }

        .tech-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            font-size: 12px;
            color: var(--text-light);
            transition: transform 0.3s ease, color 0.3s ease;
            /* Gentle float for icons */
            animation: floatIcon 4s ease-in-out infinite;
        }

        /* Staggered floating effect for odd and even icons */
        .tech-item:nth-child(odd) { animation-delay: 0s; }
        .tech-item:nth-child(even) { animation-delay: 2s; }

        .tech-item:hover {
            transform: scale(1.15) translateY(-5px);
            color: #ffffff;
            cursor: pointer;
        }

        .tech-item i {
            font-size: 34px;
        }

        .devicon-github-original { color: #ffffff; }

        /* Footer Menu */
        .footer-menu {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            font-size: 16px;
            color: var(--text-light);
            opacity: 0;
            animation: slideUpFade 1s cubic-bezier(0.2, 0.8, 0.2, 1) 0.9s forwards;
        }

        .footer-menu .dot {
            color: var(--brand-blue);
            font-size: 10px;
        }
        
        .footer-menu .blue-text {
            color: var(--brand-blue);
            font-weight: 600;
        }

        /* =========================================
           KEYFRAME ANIMATIONS
           ========================================= */

        /* 1. Gradient breathing background */
        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* 2. Floating text (retains rotation) */
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(var(--rot)); }
            50% { transform: translateY(-12px) rotate(var(--rot)); }
        }

        /* 3. Initial Slide Up Fade-in */
        @keyframes slideUpFade {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* 4. Glowing text effect */
        @keyframes textGlow {
            0% { text-shadow: 0 0 5px rgba(29, 161, 242, 0.2); }
            100% { text-shadow: 0 0 20px rgba(29, 161, 242, 0.6); }
        }

        /* 5. Subtle tech icon float */
        @keyframes floatIcon {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-6px); }
        }

    </style>
</head>
<body>

<div class="banner-container">
    <div class="banner-overlay"></div>
    
    <!-- Left Floating Text -->
    <div class="handwritten left">
        Build<br>Learn<br>Improve
        <span class="blue-code">&lt;/&gt;</span>
    </div>

    <!-- Right Floating Text -->
    <div class="handwritten right">
        Same<br>Dreams<br>Bigger<br>Plans
    </div>

    <div class="content">
        <!-- Name -->
        <h1>SUMAN <span class="blue-text">KUMAR YADAV</span></h1>

        <!-- Roles -->
        <div class="roles">
            <span><i class="fa-solid fa-code"></i> Software Developer</span>
            <span class="separator">|</span>
            <span><i class="fa-solid fa-brain"></i> AI/ML Enthusiast</span>
            <span class="separator">|</span>
            <span><i class="fa-solid fa-layer-group"></i> System Design</span>
            <span class="separator">|</span>
            <span><i class="fa-solid fa-laptop-code"></i> Full-Stack Developer</span>
            <span class="separator">|</span>
            <span><i class="fa-solid fa-lightbulb"></i> Problem Solver</span>
        </div>

        <!-- Tagline -->
        <div class="tagline">
            <div class="horizontal-line"></div>
            Turning Ideas Into Real-World Solutions
            <div class="horizontal-line"></div>
        </div>

        <!-- Tech Stack -->
        <fieldset class="tech-stack-box">
            <legend>TECH STACK</legend>
            <div class="tech-icons">
                <div class="tech-item"><i class="devicon-java-plain colored"></i> Java</div>
                <div class="tech-item"><i class="devicon-python-plain colored"></i> Python</div>
                <div class="tech-item"><i class="devicon-javascript-plain colored"></i> JavaScript</div>
                <div class="tech-item"><i class="devicon-react-original colored"></i> React</div>
                <div class="tech-item"><i class="devicon-nodejs-plain colored"></i> Node.js</div>
                <div class="tech-item"><i class="devicon-mongodb-plain colored"></i> MongoDB</div>
                <div class="tech-item"><i class="devicon-mysql-plain colored"></i> MySQL</div>
                <div class="tech-item"><i class="devicon-git-plain colored"></i> Git</div>
                <div class="tech-item"><i class="devicon-github-original"></i> GitHub</div>
                <div class="tech-item"><i class="devicon-vscode-plain colored"></i> VS Code</div>
            </div>
        </fieldset>

        <!-- Bottom Menu -->
        <div class="footer-menu">
            <div class="horizontal-line" style="width: 40px;"></div>
            Learn 
            <i class="fa-solid fa-circle dot"></i> Build 
            <i class="fa-solid fa-circle dot"></i> Solve 
            <i class="fa-solid fa-circle dot"></i> <span class="blue-text">Grow</span>
            <div class="horizontal-line" style="width: 40px;"></div>
        </div>
    </div>
</div>

</body>
</html>

# 👋 Hi, I'm Suman Kumar Yadav

### **Software Developer • System Design • Full-Stack Developer • Problem Solver**

I'm a developer focused on **building practical software, solving real-world problems, and continuously improving my development skills.** 🚀

My interests sit at the intersection of:

**Artificial Intelligence × Full-Stack Development × Data Structures & Algorithms × Data Analytics**

I'm currently exploring **Java, Python, JavaScript, React, Node.js, SQL, MongoDB, and AI/ML**, while building projects and solving problems to strengthen my fundamentals.

> 💡 **Learn. Build. Solve. Repeat.**


---

## 🚀 About Me

* 🎓 Pursuing **BCA in Artificial Intelligence & Data Science**
* 💻 Currently strengthening my **DSA & Software Development** fundamentals
* 🧩 Solved **50+ problems on LeetCode**
* 🌐 Learning **Full-Stack Web Development**
* 🤖 Exploring **AI & Data Science**
* 📚 Currently working on improving my **Java, JavaScript and problem-solving skills**
* 🎯 Goal: Become a **Software Developer**
* ⚡ Believe in: **Learn → Build → Practice → Improve**

---

## 🛠️ Tech Stack

### 💻 Programming Languages

<p>
  <img src="https://skillicons.dev/icons?i=java,python,javascript" />
</p>

### ⚛️ Web Development

<p>
  <img src="https://skillicons.dev/icons?i=html,css,js,react,nodejs,nextjs" />
</p>

### ⚙️👨‍💻Database & Tools

<p>
  <img src="https://skillicons.dev/icons?i=mongodb,mysql,git,github,vscode" />
</p>

---

## 🧠 Data Structures & Algorithms

Currently practicing DSA with **Java** and focusing on understanding patterns rather than memorizing solutions.

### Topics I'm Practicing

* Arrays
* Strings
* Hashing
* Sorting
* Searching
* Recursion
* Two Pointers
* Binary Search
* Basic Data Structures
* Problem Solving

🏆 **50+ LeetCode Problems Solved**

---

## 🌐 Web Development Journey

Currently learning Full-Stack Web Development and building my fundamentals from scratch.

### Learning Path

```text
HTML
  ↓
CSS
  ↓
JavaScript
  ↓
React
  ↓
Node.js
  ↓
MongoDB
  ↓
Full-Stack Projects
```

I'm currently working through the **Sigma Web Development** learning journey and practicing by building small projects and exercises.

---

## 🚀 Projects

### 🚕 AeroRide

A ride-booking application concept inspired by modern ride-hailing platforms, with a focus on a simple user experience and AI-powered voice interaction.

**Focus:** Web Development • AI • APIs

---

### 📚 StudyConnect

A student-focused learning platform designed to help students access notes, practice questions, and AI-powered learning assistance.

**Focus:** Education • AI • Web Development

---

### 🚌 Smart Campus Bus

A concept for improving college transportation by helping students access campus bus routes and transportation information more efficiently.

**Focus:** Problem Solving • Smart Campus • Technology

---

## 📈 My Learning Goals

* [ ] Master DSA patterns
* [ ] Solve 100+ LeetCode problems
* [ ] Build strong Java fundamentals
* [ ] Become confident with React
* [ ] Learn backend development
* [ ] Build production-level projects
* [ ] Learn more about AI/ML
* [ ] Contribute to Open Source

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=suman0001yadav-ind&show_icons=true&theme=tokyonight" />
</p>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=suman0001yadav-ind&theme=tokyonight" />
</p>

---

## 🏆 Coding Profiles

* 💻 **LeetCode:** 50+ problems solved
* 🐙 **GitHub:** Building consistently and documenting my learning journey

---

## 📫 Connect With Me

<p>
  <a href="https://github.com/suman0001yadav-ind">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
  </a>
  <a href="https://linkedin.com/in/suman-kumar-yadav-856469366">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/>
  </a>
</p>

---

### 💡 "Consistency beats intensity."

I'm learning, building, and improving every day. 🚀
