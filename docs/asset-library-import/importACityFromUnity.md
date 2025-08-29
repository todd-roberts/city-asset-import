# Unity → Blender → Horizon Worlds: City Import & Cleanup (Part 1: Unity)

Rough‑draft script + shot list up to selecting a clean city section inside Unity. This stands as its own tutorial (separate from the lighting tutorial).

---

## 0) Intro: What we’re doing & why

**On‑camera beat (10–20s):**

* “I’m building a cool new city scene for my Horizon Worlds world. Rather than model a whole city, I bought a modular city pack and I’m going to extract just one great block from it, clean it up, and move it down the pipeline: Unity → Blender → HW.”
* “This video is Part 1 and lives entirely in Unity. We’ll import the pack, make the demo scene viewable—even if it’s all pink—and isolate the chunk we want.”

**Lower‑third:** Unity → Blender → HW pipeline (Part 1: Unity)

---

## 1) Import the city via Package Manager

**Narration:** “I purchased a city asset from the Unity Asset Store. First step: bring it into my project.”

**Steps:**

1. Open **Window → Package Manager**.
2. Switch to **My Assets**.
3. Locate the city pack → click **Download** (if needed) → **Import**.
4. In the import dialog, accept defaults for now; we’ll trim later.

**Shots to capture:**

* ![Open Package Manager](images/u2b_hw_pkg_mgr_open.jpg)
* ![Asset in Package Manager (Import visible)](images/u2b_hw_pkg_mgr_import.jpg)
* ![Project panel → the asset’s root folder](images/u2b_hw_project_root.jpg)

**Callout box:** “Goal now is reconnaissance: open a demo scene to see what’s inside.”

---

## 2) Explore the demo scene (it’s pink—don’t panic)

**Narration:** “I open the included demo scene to understand scale and layout. In URP projects, third‑party assets often load pink due to incompatible shaders.”

**Steps:**

1. In **Project** panel, browse the asset’s **Scenes** folder (common names: *Demo*, *Sample*, *Example*, *Showcase*, *Demonstration*).
2. Open the **Demonstration** scene → everything is pink.

**Shots:**

* ![Scenes folder](images/u2b_hw_scenes_folder.jpg)
* ![Pink demo scene](images/u2b_hw_pink_demo.jpg)

**Explain:**

* “Pink ≠ broken meshes. It’s usually a shader pipeline mismatch.”
* Link the official **URP Render Pipeline Converter** doc: *(we tried this first)*

  * [https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@12.0/manual/features/rp-converter.html](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@12.0/manual/features/rp-converter.html)

**Outcome:** “In my case, the converter didn’t fix it and I saw shader errors (e.g., ‘out of memory while parsing …’). So I’ll use a fast workaround just to *see* the city.”

---

## 3) Quick visibility workaround: swap to URP/Unlit

**Narration:** “I only need to preview geometry and pick a good block. I don’t need the asset’s fancy custom shaders.”

**Steps:**

1. In the asset’s **Materials** folder, find a shared color material (in my case, it’s literally named **Color**).
2. Select it → In the **Inspector**, change **Shader** to **Universal Render Pipeline/Unlit**.
3. Return to the demo scene; meshes are now visible with flat color.

**Shots:**

* ![Materials folder](images/u2b_hw_materials_folder.jpg)
* ![Change shader to URP/Unlit](images/u2b_hw_material_unlit.jpg)
* ![City visible after shader swap](images/u2b_hw_city_visible.jpg)

**Callout:** “This doesn’t match the author’s intended look—and that’s okay. We only need visibility to choose what to export. Blender and HW won’t use these shaders anyway.”

**Sidebar: quick grab alternative**

* If you only need single props: find **Textures** and **Meshes/Models/FBX** folders, right‑click an **FBX → Show in Explorer** and copy it out. For the city block approach, continue below.

---

## 4) Pick your city section and prune the rest

**Narration:** “The full city is far too big for Horizon Worlds. I’m going to select one strong block and delete everything else. Vehicles can wait—I can re‑import/merge them later.”

**Steps:**

1. In **Hierarchy**, identify grouped city sections (search for naming like *Block*, *District*, *Module*, or scan the parent nodes).
2. Frame a candidate area in **Scene view** (streets + sidewalks + a few buildings + a waterway if you want that vibe).
3. Duplicate the scene or **Save As** a new one: `City_Block_Selection`.
4. Delete distant blocks, skyboxes, vehicles, and FX you won’t use.
5. Keep the minimal set you plan to export (we’ll FBX this to Blender next video).

**Shots:**

* ![Full city before pruning](images/u2b_hw_before_prune.jpg)
* ![Selected section framed](images/u2b_hw_section_framed.jpg)
* ![Vehicles removed, city trimmed](images/u2b_hw_after_prune.jpg)

**Tips:**

* Keep sidewalks continuous; ensure intersections aren’t half‑deleted.
* Favor modular boundaries—tile seams that make sense for later joining.
* Note any areas with water meshes; they can need extra cleanup downstream.

**Checkpoint (speak on‑camera):**

* “This is the exact footprint I’ll take forward. Next, I’ll export this to FBX, then hop into Blender to join tiles and prep for Horizon Worlds.”

---

## 5) Appendix: Common pitfalls (mention briefly on‑camera)

* **URP/HDRP mismatches** → Pink materials; use RP Converter first, then fall back to URP/Unlit visibility.
* **Massive scenes** → Don’t bring the whole city. Decide your playable block early.
* **Vehicles/FX** → Save them for later unless they’re essential to geometry selection.
* **Folder hygiene** → Start a clean export folder now (e.g., `Exports/CityBlockA/`).

---

## 6) Asset checklist & filenames (for your editor)

* Stills:

  * `u2b_hw_pkg_mgr_open.jpg`
  * `u2b_hw_pkg_mgr_import.jpg`
  * `u2b_hw_project_root.jpg`
  * `u2b_hw_scenes_folder.jpg`
  * `u2b_hw_pink_demo.jpg`
  * `u2b_hw_materials_folder.jpg`
  * `u2b_hw_material_unlit.jpg`
  * `u2b_hw_city_visible.jpg`
  * `u2b_hw_before_prune.jpg`
  * `u2b_hw_section_framed.jpg`
  * `u2b_hw_after_prune.jpg`

**Next episode teaser:** Exporting the trimmed block to **FBX**, bringing it into **Blender** to join modular tiles, fix normals/overlaps, and prep for **Horizon Worlds**.
