---
title: Cursos
summary: Mis cursos
type: landing

cascade:
    - target:
          path: "{/courses/*/**}"
      type: docs
      params:
          show_breadcrumb: true

sections:
    - block: collection
      id: courses
      content:
          title: Cursos
          filters:
              tag: Curso
              kinds:
                  - section
      design:
          view: article-grid
          show_read_time: false
          show_date: false
          show_read_more: false
          columns: 1
---
