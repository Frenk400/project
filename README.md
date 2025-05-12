# project
[Untitled_Project.zip](https://github.com/user-attachments/files/20175927/Untitled_Project.zip)

<div align="center"><img src="./docs/workflow. png" width="700"><p>AI video generation workflow (schematic diagram needs to be replaced with actual architecture diagram)</p></div>

Build a fully automated video generation system to achieve:

Single theme input → Automatically generate complete video (including text/images/dubbing/subtitles)
Support multilingual generation in both Chinese and English
Dual mode of local deployment and API service

Milestone achievements of the core technology stack in the stage
Requirement analysis, user behavior data analysis, and determination of video generation accuracy indicators (95% material matching rate)
Core development of Python+FastAPI+Stable Diffusion to achieve synchronous generation engine for speech/image/subtitles
Test optimization Pytest+Locust completed a 20 hour stress test (QPS ≥ 15)



mermaid
Copy Code
gantt
Title Project Development Gantt Chart
dateFormat  YYYY-MM-DD
Core Stage of Section
Requirement definition: done, des1, May 1, 2025, 7d
Algorithm prototype development: active, des2, May 8, 2025, 10d
System integration testing: des3, May 20, 2025, 14d

Implementing Logic with Multimodal Generation Engine



def generate_video(topic: str) -> VideoAsset:
(Using Gemini Flash model: ml citation {ref="3,4" data="citationList"})
script = llm.generate(
Prompt=f "Create a short video script about {topic}",
Structure=ScriptSchema # Force output structured JSON
)
    
(Stable Diffusion batch inference: ml citation {ref="8" data="citationList"})
scenes = [sd.generate(prompt=scene_desc) 
for scene_desc in script['scenes']]
    

audio = tts.render(script['dialogues'])
    
return compose_assets(scenes, audio) 
﻿
