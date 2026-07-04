---
title: "Home"
layout: default
sitemap: false
permalink: /
---

<style>
.jumbotron{
    padding:3%;
    padding-bottom:10px;
    padding-top:10px;
    margin-top:10px;
    margin-bottom:30px;
}

.headshot-wrapper {
  position: relative;
  display: inline-block;
  float: right;
  margin-left: 20px;
  perspective: 1000px;
  width: 350px;
  min-width: 30%;
  max-width: 100%;
  z-index: 10;
}

.headshot-img {
  display: block;
  width: 100%;
  border-radius: 16px;
  box-shadow: 0 4px 16px rgba(0,0,0,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.headshot-wrapper:hover .headshot-img {
  box-shadow: 0 8px 30px rgba(106,130,251,0.5);
}
</style>


<div id="homeid" class="col-sm-12 col-xs-12">
<div class="headshot-wrapper">
  <img id="headshot-img" class="headshot-img" src="{{site.url}}{{site.baseurl}}/images/headshot.jpg" alt="Headshot">
</div>




<script>
// 3D tilt effect on mouse move
document.addEventListener('DOMContentLoaded', function() {
  const img = document.getElementById('headshot-img');
  const wrapper = document.querySelector('.headshot-wrapper');
  
  if (!img || !wrapper) return;
  
  wrapper.addEventListener('mousemove', function(e) {
    const rect = wrapper.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    
    // Calculate center point
    const centerX = rect.width / 2;
    const centerY = rect.height / 2;
    
    // Calculate normalized position from center (-1 to 1)
    const xPercent = (x - centerX) / centerX;
    const yPercent = (y - centerY) / centerY;
    
    // Calculate distance from center (0 to 1)
    const distance = Math.min(1, Math.sqrt(xPercent*xPercent + yPercent*yPercent));
    
    // Apply tilt based on mouse position - inverse Y for natural feel
    // Max tilt of 8 degrees for subtle effect
    const tiltY = xPercent * 8 * distance;
    const tiltX = -yPercent * 8 * distance;
    
    // Apply transform - scaled based on distance from center
    const scale = 1 - (distance * 0.02); // Very slight scaling
    img.style.transform = `perspective(1000px) rotateX(${tiltX}deg) rotateY(${tiltY}deg) scale(${scale})`;
  });
  
  wrapper.addEventListener('mouseleave', function() {
    // Reset transform on mouse leave
    img.style.transform = 'perspective(1000px) rotateX(0) rotateY(0) scale(1)';
  });
});
</script>

<div style="text-align:justify">
### about me
Hi! Thank you for checking out my website! I'm Prajit Rajkumar, a student at [UC San Diego](https://ucsd.edu/). 

I'm pursuing degrees in [Biology with a Specialization in Bioinformatics](https://biology.ucsd.edu/education/undergrad/major-minor-programs/majors/requirements/bioinformatics/index.html) and [Mathematics-Computer Science](https://math.ucsd.edu/students/undergraduate/ma30-math-computer-science-b-s). 

Outside of class, I'm heavily involved with research as part of the [Dorrestein Lab](https://dorresteinlab.ucsd.edu/) at UCSD's [Skaggs School of Pharmacy & Pharmaceutical Sciences](https://pharmacy.ucsd.edu/), where I mainly focus on computational metabolomics. I've been fortunate to have had the opportunity to contribute to and lead a number of [publications](https://praj.it/publications/) in this group, and I've received grants from OpenAI and Google DeepMind for my work. I've also been fortunate enough to receive a [Barry Goldwater Scholarship](https://goldwaterscholarship.gov/) for my work, which would not have been possible without the support of my amazing mentors, including [Pieter Dorrestein](https://pharmacy.ucsd.edu/faculty/dorrestein), [Haoqi (Nina) Zhao](https://profiles.stanford.edu/nina-zhao), [Daniel-Domingo Fernández](https://de.linkedin.com/in/ddomingof), and many more!

I've continued my work in this field over the course of an internship at [Enveda](https://enveda.com/), during which I leveraged my research experience to help solve problems related to drug discovery. I returned to Enveda in Spring 2026 to work on frontier machine learning research for natural product discovery. Currently, I'm visiting at MIT, working on ML for mass spectrometry under Yunha Hwang.

I'm also passionate about teaching and giving back to the academic community that has shaped me, which has led me to work as a [Supplemental Instruction Leader](https://aah.ucsd.edu/supplemental-instruction/index.html) for various mathematics courses as well as lead UCSD's [Bioinformatics Club](https://ubicucsd.github.io/) as Vice President. 

In my free time, I like playing chess, long distance running, and watching anime.
</div>


<!-- <div class="jumbotron">
### Selected Publications
{% bibliography -f articles -q @*[selected=True]  %}
</div> -->
