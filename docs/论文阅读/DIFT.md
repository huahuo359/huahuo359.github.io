# DiFT: Differentiable Differential Feature Transform for Multi-View Stereo

!!! note "Interduction"

    - **problem:** Image-based 3D reconstruction of physical objects with complex appearance is a key problem in computer vision and graphics
    - 通过密集采样获得独特的差异结构线索
    - 困难： Specifically, it is highly
        challenging to handle the appearance that **varies considerably with the lighting and/or view conditions（变化的外观和视角）**, **textureless regions（无纹理区域）** and **complex occlusions（复杂遮挡）**， 一些其他方法通常假设光线的反射是漫反射。
    -  convert the photo-metric information into low-level multi-view stereo features.
    -  We focus on learning **high-quality local
    features**, and delegate subsequent processing (e.g., spatial aggregation/view selection) to any existing learning-/non-learning-based multi-view stereo pipeline. 




!!! note "Related Work"
    - **Depth from Densely Sampled Views**
    - **Features for Multi-View Stereo**
    - **ACQUISITION DEVICE**
    - **RENDERING EQUATION(渲染方程式)**


!!! success "Depth from Densely Sampled Views"
    - 传统多视图重建的方法：it does
    not explicitly exploit the rich, depth-related structures in densely sampled near-by views, leading to sub-optimal geometric reconstruction. (没有充分利用所有的信息，会导致一个次优的几何重建)
    - 流程:
          1. The first step extracts useful local structural cues， 必须额外注意视图变化和外观变化。
          2. The next step aggregates
            local information to compute a global representation 
          3. The final step is
            to generate the depth according to its relationship with the global information  