---
layout: page
permalink: /adventure/
title: adventure
description: University, work, travel, and hiking highlights on the map.
nav: true
nav_order: 5
---

## Adventure Map

<style>
  .adventure-map-shell {
    margin: 1rem 0 1.5rem;
    padding: 0.65rem;
    border: 1px solid var(--global-divider-color);
    border-radius: 14px;
    background:
      radial-gradient(circle at 8% 14%, color-mix(in srgb, var(--global-theme-color) 25%, transparent), transparent 38%),
      radial-gradient(circle at 90% 0%, color-mix(in srgb, var(--global-theme-color) 16%, transparent), transparent 35%),
      var(--global-card-bg-color);
    box-shadow: 0 14px 34px rgba(0, 0, 0, 0.1);
  }

  .adventure-map-frame {
    position: relative;
    width: 100%;
    border-radius: 10px;
    overflow: hidden;
    border: 1px solid color-mix(in srgb, var(--global-divider-color) 80%, transparent);
    aspect-ratio: 16 / 10;
    min-height: 340px;
  }

  .adventure-map-frame iframe {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    border: 0;
    display: block;
  }

  @media (max-width: 768px) {
    .adventure-map-shell {
      padding: 0.45rem;
    }

    .adventure-map-frame {
      min-height: 300px;
      aspect-ratio: 4 / 3;
    }
  }
</style>

<div class="adventure-map-shell">
  <div class="adventure-map-frame">
    <iframe
      src="https://www.google.com/maps/d/u/0/embed?mid=1y-hszeuJ6pXkxH2z5rfPtehrBU-kzuo&ehbc=2E312F"
      loading="lazy"
      referrerpolicy="no-referrer-when-downgrade"
      title="Adventure locations map"
    ></iframe>
  </div>
</div>
