---
layout: page
title: MamboLanding
description: A self-landing UAV people detector.  
img: /assets/img/cover-project1.jpg
---

Almost every drone autonomous navigation system is today highly dpenedent from a gps system that allows to have some kind of reference point so it can have some notion auto-localization. Nevertheless, depending of this kind of sensors can be many times highly unaccurate, specially for tasks like landing on a specific point without prior map knoledge.  
In this project we proposed a navigation system for a low cost drone that only requires a front monocular camera and with that, is able to detect, aproach and land in front a person.
To this end we implement a Single Shot Detector (SSD) algorithm and a trained Mobilenet CNN for vision task, and the posterior navigation algorithm based on this detections.


<!---
    ---
    layout: page
    title: Project
    description: a project with a background image
    img: /assets/img/12.jpg
    ---
--->

<div class="img_row">
    <img class="col one left" src="{{ site.baseurl }}/assets/img/cover-project1.jpg" alt="" title="cover image"/>
    <!---<img class="col one left" src="{{ site.baseurl }}/assets/img/2.jpg" alt="" title="example image"/>--->
    <img class="col two left" src="{{ site.baseurl }}/assets/img/mambo.jpg" alt="" title="example image"/>
</div>
<div class="col three caption">
    Pictures of parrot mambo drone.  
</div>

<h3>Vision </h3>

A cool thing about mobilenet is that the architecture tries to preserve the main advantage of resnets by putting a residual block allowing to avoid vanishing or exploding gradient during training, and at the same time uses only 1x1 convololutions the beginning and at the end of each 3x3 kind of layer, witch  considerably reduces the number of channels and therefore, the number of parameters and inference time.
The model was trained on CIFAR-10, so the network has a 20 class output.

<div class="img-row">
    <img class="col four" src="{{ site.baseurl }}/assets/img/mobilenet.jpg" alt="" title="example image"/>
    <!---<img class="col one left" src="{{ site.baseurl }}/assets/img/11.jpg" alt="" title="example image"/>--->
</div>
<div class="col three caption">
    Mobilennet arquitecture
</div>

Once we had built the mobilenet, the following step is use it to build the SSD, witch will have an output of 24 channels, 20 for the number of clases plus the boundary box (cx, cy, w, h).  
With the combination of the SSD plus mobilenet, we reached an inference time of 4 miliseconds per image.

<h3>Navigation: 4 defined states </h3>


<div class="img_row">
    <img class="col three left" src="{{ site.baseurl }}/assets/img/secuencia.jpg" alt="" title="example image"/>
</div>


<div class="col three caption">
    Visualization of the 4 states of navigation
</div>

<br/><br/>

<div class="img_row">
    <img class="col three left" src="{{ site.baseurl }}/assets/img/Selection.jpg" alt="" title="example image"/>
</div>


<div class="col three caption">
    Capture from a navigation test drive on third and first person perspective. Check the full video <a href="https://www.youtube.com/watch?list=PL5PIk24t1cVYq7BGWIc3eMJ8nIkloUO0Y&v=sV9nGOG_bL0&feature=emb_title" target="_blank">here</a>
</div>

<h3>Metrics</h3>
After the course project, we took the drone to the <a href="https://www.uandes.cl/carrera/kinesiologia/investigacion/" target="_blank">biomechanics lab (LIBFE)</a> to measure how well the trayectory behave under more difficult circunstances like occluded person goal or a dinamic kind of goal and we found that in the occluded case the system is still capable of landing near the goal, although it did missed in some parts of the simulations, wich is why we coul see in the fist 2 images some weird trayectories.
In the dynamic case, as it can be seen from the third image, the system doesn't respond well when the target is moving.

<div class="img_row">
    <img class="col one left" src="{{ site.baseurl }}/assets/img/target.jpg" alt="" title="cover image"/>
    <!---<img class="col one left" src="{{ site.baseurl }}/assets/img/2.jpg" alt="" title="example image"/>--->
    <img class="col two left" src="{{ site.baseurl }}/assets/img/mambo.jpg" alt="" title="example image"/>
</div>
<div class="col three caption">
    Mambo and target  
</div>

<div class="img_row">
    <img class="col one left" src="{{ site.baseurl }}/assets/img/estatico_a.jpg" alt="" title="cover image"/>
    <img class="col one left" src="{{ site.baseurl }}/assets/img/estatico_c.jpg" alt="" title="example image"/>
    <img class="col one left" src="{{ site.baseurl }}/assets/img/dinamico.jpg" alt="" title="example image"/>
</div>
<div class="col three caption">
    Trajectories. The firs 2 were simulated with ocluded target and the third was a simulation with dynamic target. 
</div>
