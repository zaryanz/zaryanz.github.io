---
layout: page
title: Projects
share-title: Aryan Singh | Projects
---

---

<h2 class="mb-0">Projects I have built or worked on</h2>

<div style="flex-direction:row; margin-top: 1rem;">
<a href="https://apps.apple.com/in/app/for-all-community/id1658745332" target="_blank" style="text-decoration: none;">
<img src="/assets/img/gptw_app_icon.webp" alt="FOR ALL COMMUNITY application icon" class="project-icon" />
</a>

<a href="https://apps.apple.com/in/app/travokarma/id1596474556" target="_blank" style="text-decoration: none;">
<img src="/assets/img/travokarma_app_icon.webp" alt="Travokarma application icon" class="project-icon" />
</a>

<a href="https://apps.apple.com/in/app/fikaa-investment-app-for-women/id1641668238" target="_blank" style="text-decoration: none;">
<img src="/assets/img/fikaa_app_icon.webp" alt="GenWE application icon" class="project-icon" />
</a>

<a href="https://apps.apple.com/in/app/genwe/id1537440686" target="_blank" style="text-decoration: none;">
<img src="/assets/img/genwe_app_icon.webp" alt="GenWE application icon" class="project-icon" style="border: 0.5px solid #d3d3d3;" />
</a>

<a href="https://www.asttaas.com/" target="_blank" style="text-decoration: none;">
<img src="/assets/img/ast_logo.webp" alt="AST TaaS Web Portal icon" class="project-icon" />
</a>

<a href="https://www.remassis.com/" target="_blank" style="text-decoration: none;">
<img src="/assets/img/remassis_logo.webp" alt="Remassis app icon" class="project-icon" style="width: 8rem" />
</a>
</div>
---
## Personal Projects
<div class="personal-projects-container">
{% for project in site.data.personal-projects %}
<div class="custom-card">
  <a href="#">
  <img src="{{ project.image }}" alt="{{ project.name }}" />
  </a>
  <div class="custom-card-text-container">
    <h3>{{ project.name }}</h3>
    <p>{{ project.description }}</p>
    <a
      href="{{ project.github_link }}"
      class="d-flex flex-direction-row align-items-center mt-3 mb-2"
      ><i class="fab fa-github mr-1"></i>
      <p>GitHub Link</p></a
    >
  </div>
</div>
{% endfor %}
</div>
