---
layout: page
permalink: /teaching/
title: Teaching
description: Statement of Teaching Interests and Plans (See Previously Taught Course Materials at the Bottom)
nav: true
nav_order: 6
calendar: true
---

### A. Philosophy and Core Values ###

My teaching philosophy is grounded in the belief that students learn best when actively engaging with real-world examples.  My goals as an educator are to foster deep critical thinking, cultivate the ability to deconstruct complex problems, and nurture a challenge-driven mindset.  Because medical imaging sits at the intersection of physics, computation, and clinical application, the ability to integrate ideas across domains is essential for innovation.  I view my teaching role as that of a mentor and facilitator, creating a classroom of guided discovery where students learn from existing knowledge while gaining the confidence to create new knowledge.  Ultimately, I aim to train a new generation of engineers who view imaging not as a collection of modalities, but as a coherent framework of inverse problems rooted in physics and computation.

### B. Teaching Approach and Methods ###

I emphasize deep conceptual understanding through active, problem-based learning.  Students internalize complex material most effectively when mathematical theory is paired with computational implementation that mirrors how engineers analyze real systems.  This philosophy guided the development of a graduate-level course, [***Inverse Problems in Imaging***]() (ECE 485, University of Rochester).  The course introduces the core mathematical tools from linear algebra and optimization through intuitive examples before applying them to imaging systems such as X-ray CT, MRI, electrical impedance tomography, ptychography, and ultrasound tomography.  By highlighting the shared mathematical structure across modalities, students learn to recognize unifying principles rather than memorizing isolated techniques.  Assignments are computational and cumulative, reinforcing concepts through implementation.  Instead of traditional exams, students complete project-based assessments using simulated or experimental data.  This structure promotes creativity, technical rigor, and independent problem-solving while reflecting the open-ended nature of research.

### C. Vision for an Innovative Graduate Course on Medical Imaging ###

Traditional medical imaging courses often focus on linear shift-invariant systems where Fourier and Radon transforms provide analytical closed-form solutions.  However, many modern imaging systems are either (1) [***linear but not shift-invariant***]() or (2) [***fully nonlinear***](), making them inaccessible to purely transform-based methods.  To address this gap, the [***Inverse Problems in Imaging***]() course I developed at the University of Rochester uses inverse problems as a unifying theoretical framework for analyzing both linear and nonlinear imaging systems. Within this framework, shift invariance naturally emerges as a special case that permits analytical inversion, while more complex systems are approached through [***iterative reconstruction algorithms***]() that explicitly use [***forward and adjoint operators***]() for modeling and inversion.  This approach gives students a unified understanding of imaging systems and equips them with computational tools relevant to current research and industry practice.  

### D. Commitment to Mentoring Students from Diverse Backgrounds ###

Students enter medical engineering from highly diverse academic backgrounds. I see effective teaching as meeting students where they are and supporting them as they build both competence and confidence.  At the University of Rochester, I mentored international students with limited programming experience who sought to bring ultrasound tomography to low-resource clinical settings. Through individualized guidance and structured learning, they developed strong computational and analytical skills, ultimately leading independent projects.  This experience reinforced my belief that mentorship can empower students not only to succeed academically but also to broaden the global reach of engineering innovation.  Within my own independent research program, I will continue fostering this inclusive, mentorship-driven model—helping students from diverse backgrounds integrate physics and computation to advance imaging science and human health.  


{%- comment -%}
{% include calendar.liquid calendar_id='test@gmail.com' timezone='Asia/Shanghai' %}
{%- endcomment -%}


{% include courses.liquid %}
