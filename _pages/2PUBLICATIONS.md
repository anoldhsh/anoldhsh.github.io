---
layout: page
title: PUBLICATIONS
permalink: /PUBLICATIONS/
image: Publications_0731.jpg
---

<div id="button-container">
  <button id="toggle-summary-btn" class="tag-filter-btn" data-filter="all">Show Research Project Summary</button>
</div>

<div id="research-summary" class="summary-hidden">
  <h4>RESEARCH PROJECT SUMMARY</h4>
  
  <div class="research-section">
    <b>Blurring the Boundary Between Reality and Virtuality: Research on Novel Haptic Devices</b>
    <ul>
      <li>Creation and evaluation of a small, lightweight haptic system that uses electrical muscle stimulation (EMS) combined with biomechanical simulation to stimulate multiple muscles simultaneously, providing users with precise directional haptic force feedback [c.5, w.4]</li>
      <li>Improvement of the response time limitations of previous thermal haptic devices by using motorized Peltier modules, creating a device capable of providing a high level of realism in situations requiring rapid sensory transitions [c.8, w.1]</li>
      <li>Development of exemplary VR applications utilizing haptic devices in industrial settings [c.8, w.4] and VR game content [c.5, c.8, w.1]</li>
    </ul>
  </div>

  <div class="research-section">
    <b>Towards Seamless Walking in Virtual Environments: Redirected Walking (RDW)</b>
    <ul>
      <li>Development and usability testing of various haptic systems to enhance the obstacle avoidance capability of RDW technology, overcoming the physical limitations of real-world space, thereby enhancing the seamless walking experience</li>
      <li>Creation of haptic devices that can provide vestibular stimulation (galvanic, bone conduction vibration, thermal) [c.1, c.3, p.2, pa.1], olfactory stimulation, auditory stimulation [j.2, p.1], and visual stimuli with optical flow [j.1], along with algorithms to determine the optimal type and timing of stimulation</li>
      <li>Further implementation of algorithms to improve RDW's spatial scalability by predicting user paths through real-time sensing of walking data and deep learning-based user path prediction – responsible for implementing the real-time gait sensor streaming system [p.4]</li>
    </ul>
  </div>

  <div class="research-section">
    <b>Utilizing Haptic Technology for Accessibility</b>
    <ul>
      <li>Development and implementation of a hat-shaped haptic device that induces the “Hanger reflex” to expand the field of vision for people with low vision [c.6]</li>
      <li>Development of an intelligent walker that integrates pressure sensors, linear actuators, and motorized wheels, dynamically changing its form to match the patient's intent and the surrounding environment, aimed at improving rehabilitation performance for patients with lower body motor impairments [w.2]</li>
    </ul>
  </div>

  <div class="research-section">
    <b>Interactions Between Autonomous Vehicles (AVs) and People</b>
    <ul>
      <li>Development and evaluation of a haptic system that activates muscles via EMS based on the content and movement of the vehicle to address motion sickness, a major limitation of VR use in AVs [c.4, w.3]</li>
      <li>Development and evaluation of an in-car VR locomotion system that allows users to freely explore the environment, rather than simply observing content on predetermined routes [p.3, cc.1, cc.2]</li>
      <li>Creation and distribution of a comprehensive dataset of AV passengers’ real-time needs and biometric signals [c.7]</li>
      <li>Development and design evaluation of an AR-based virtual agent for communication between AVs and pedestrians [c.2]</li>
    </ul>
  </div>

  <div id="button-container">
    <button id="hide-summary-btn" class="tag-filter-btn" style="margin-top: 20px;" data-filter="all">Hide</button>
  </div>

</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const toggleButton = document.getElementById('toggle-summary-btn');
  const hideButton = document.getElementById('hide-summary-btn');
  const summaryDiv = document.getElementById('research-summary');

  toggleButton.addEventListener('click', function() {
    if (summaryDiv.classList.contains('summary-hidden')) {
      summaryDiv.classList.remove('summary-hidden');
      summaryDiv.classList.add('summary-visible');
    }
  });

  hideButton.addEventListener('click', function() {
    summaryDiv.classList.remove('summary-visible');
    summaryDiv.classList.add('summary-hidden');
    toggleButton.textContent = 'Show Research Project Summary';
  });

  const tagColors = {
    'Haptics': '#A3E4F2',
    'Locomotion': '#FFDAB9',
    'AutomotiveUX': '#A7FAC8',
    'Accessibility': '#FFD580',
    'Conference': '#B0E0E6',
    'Journal': '#CBF3D2',
    'Poster&Workshop': '#89CFF0',
    'FA': '#C3B1E1',
    'Award': '#FFFACD',
  };
  
  const filterButtons = document.querySelectorAll('.tag-filter-btn');
  filterButtons.forEach(function(btn) {
    const filter = btn.getAttribute('data-filter');
    const btnColor = tagColors[filter] || '#f0f0f0'; 
    btn.style.backgroundColor = btnColor;
    btn.style.fontWeight = 'bold'; 

    btn.addEventListener('click', function() {
      filterButtons.forEach(function(b) {
        b.classList.remove('active');
      });
      
      if (filter !== 'all') {
        btn.classList.add('active');
      }

      const publications = document.querySelectorAll('.publication-container');
      publications.forEach(function(pub) {
        if (filter === 'all' || pub.getAttribute('data-tags').split(' ').includes(filter)) {
          pub.classList.remove('hidden');
          pub.style.opacity = 1; 
        } else {
          pub.classList.add('hidden');
          pub.style.opacity = 0;
        }
      });
    });
  });

  const publications = document.querySelectorAll('.publication-container');
  publications.forEach(function(pub) {
    const tags = pub.getAttribute('data-tags').split(' ');
    const tagsContainer = document.createElement('div');
    tagsContainer.classList.add('publication-tags');

    tags.forEach(function(tag) {
      const tagElement = document.createElement('span');
      tagElement.classList.add('publication-tag');
      tagElement.textContent = tag;

      const tagColor = tagColors[tag] || '#f0f0f0';
      tagElement.style.backgroundColor = tagColor;
      tagElement.style.fontWeight = 'bold';
      tagsContainer.appendChild(tagElement);
    });

    const pubText = pub.querySelector('.publication-text');
    if (pubText) {
      pubText.insertBefore(tagsContainer, pubText.firstChild);
    }
  });
});
</script>

<style>
  #button-container {
    display: flex;
    justify-content: center;
    margin-top: -15px;
  }
  
  .summary-hidden {
    max-height: 0;
    opacity: 0;
    margin-top: -50px;
    margin-bottom: -50px;
    overflow: hidden;
    transition: max-height 0.4s ease, opacity 0.4s ease;
  }

  .summary-visible {
    max-height: 10000px;
    opacity: 1;
    margin-bottom: 50px;
    transition: max-height 0.4s ease, opacity 0.4s ease;
  }

  #research-summary {
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: #f7f7f7;
    box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
    margin-top: 20px;
    overflow: hidden;
  }

  .publication-container {
    transition: opacity 0.2s ease, max-height 0.2s ease, transform 0.3s ease;
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 5px;
    opacity: 1;
    max-height: 800px; 
    overflow: hidden;
    transform: scaleY(1); 
  }

  .hidden {
    opacity: 0;
    transform: scaleY(0);
    max-height: 0;
    padding: 0;
    margin: 0;
    overflow: hidden;
    transition: opacity 0.2s ease, max-height 0.2s ease, transform 0.3s ease;
  }

  .publication-tags {
    margin-top: 10px;
    font-family: Arial, sans-serif;
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
  }

  .publication-tag {
    display: inline-block;
    padding: 2px 6px;
    background-color: #f0f0f0;
    border-radius: 5px;
    font-size: 12px;
    color: #555;
    margin-right: 4px;
    margin-bottom: 4px;
  }

  .publication-image {
    flex: 1;
    width: 160px;
  }

  .publication-text {
    flex: 3;
    font-family: Arial, sans-serif;
    color: #333;
    line-height: 1.5;
  }

  .publication-image img {
    width: 100%;
    height: auto;
    aspect-ratio: 16 / 9;
    object-fit: cover;
    border-radius: 5px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }

  @media (max-width: 768px) {
    .publication-container {
      flex-direction: column;
    }

    .publication-image {
      width: 100%;
    }

    .publication-image img {
      height: auto;
      aspect-ratio: 16 / 9;
    }
  }

  #tag-filters {
    margin-bottom: 20px;
  }

  .tag-filter-btn {
    cursor: pointer;
    padding: 4px 8px;
    background-color: #f0f0f0;
    border: 0px solid #ddd;
    border-radius: 5px;
    font-size: 15px;
    color: #555;
    margin-right: 8px;
    margin-bottom: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }

  .tag-filter-btn:hover {
    scale: 1.05;
    transition: scale 0.1s ease-in-out;
  }

  .tag-filter-btn.active {
    border: 2px solid #555;
  }
</style>

# CONFERENCES & PUBLICATIONS

<div id="tag-filters">
  <button class="tag-filter-btn" data-filter="all">Reset_Filter</button>

<button class="tag-filter-btn" data-filter="Haptics">Haptics</button>
<button class="tag-filter-btn" data-filter="Locomotion">Locomotion</button>
<button class="tag-filter-btn" data-filter="AutomotiveUX">Automotive_UI_UX</button>
<button class="tag-filter-btn" data-filter="Accessibility">Accessibility</button>

<button class="tag-filter-btn" data-filter="Conference">Conference</button>
<button class="tag-filter-btn" data-filter="Journal">Journal</button>
<button class="tag-filter-btn" data-filter="Poster&Workshop">Poster&Workshop</button>

<button class="tag-filter-btn" data-filter="FA">FA</button>
<button class="tag-filter-btn" data-filter="Award">Award</button>

</div>

<div class="publication-container" data-tags="Haptics Conference">
  <div class="publication-image">
    <img src="/images/FlipPelt_UIST.gif" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[c.8] Flip-Pelt: Motor-Driven Peltier Elements for Rapid Thermal Stimulation and Congruent Pressure Feedback in Virtual Reality</b></font><br>
    <font size="3" style="color:dark_gray;">Kang, S., Kim, G., <strong>Hwang, S.</strong>, Park, J., Elsharkawy, A., and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>UIST '24: Proceedings of the ACM Symposium on User Interface Software and Technology</i></u> - <a href="https://doi.org/10.1145/3654777.3676363"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Poster&Workshop FA">
    <div class="publication-image">
      <img src="/images/ProposeTelePulse.png" alt="Research Image">
    </div>
    <div class="publication-text">
      <font size="4"><b>[w.4] Proposal of a Framework for Enhancing Teleoperation Experience with Biomechanical Simulation-Based Electrical Muscle Stimulation in Virtual Reality</b></font>
      <br>
      <font size="3" style="color:dark_gray;"><strong>Hwang, S.</strong>, Kang, S., Oh, J., Park, J., Shin, S., Yiyue Luo, Joseph DelPreto, Wojciech Matusik, Daniela Rus, and Kim, S.</font><br>
      <font size="3" style="color:gray;"><u><i>UbiComp/ISWC '24 Adjunct</i></u> - <a href="https://doi.org/10.1145/3675094.3678380"><strong>Link</strong></a></font>
    </div>
  </div>

<div class="publication-container" data-tags="Haptics AutomotiveUX Poster&Workshop">
  <div class="publication-image">
    <img src="/images/In-Vehicle_MS.png" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[w.3] Adaptive In-Vehicle Virtual Reality for Reducing Motion Sickness: Manipulating Passenger Posture During Driving Events</b></font>
    <br>
    <font size="3" style="color:dark_gray;">Elsharkawy, A., Ataya, A., Yeo, D., Seong, M., <strong>Hwang, S.</strong>, Joseph DelPreto, Wojciech Matusik, Daniela Rus, and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>UbiComp/ISWC '24 Adjunct</i></u> - <a href="https://doi.org/10.1145/3675094.3678381"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="AutomotiveUX Conference">
  <div class="publication-image">
    <img src="/images/TimelyTale.png" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[c.7] TimelyTale: A Multimodal Dataset Assessing Passenger's Demands for Explanations in Highly Automated Vehicles </b></font>
    <br>
    <font size="3" style="color:dark_gray;">Kim, G., <strong>Hwang, S.</strong>, Seong, M., Yeo, D., Daniela Rus, and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>Proceedings of the ACM on IMWUT</i></u> - <a href="https://dl.acm.org/doi/10.1145/3678544"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Accessibility Poster&Workshop">
  <div class="publication-image">
    <img src="/images/HapticWalker.jpeg" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[w.2] Intelligence Walker: A Seamless Mobility Assist Device for the Elderly</b></font>
    <br>
    <font size="3" style="color:dark_gray;">Choi, Y., Yeo, D., <strong>Hwang, S.</strong>, Seong, M.,
      Moon, J., Yiyue Luo, Wojciech Matusik, Daniela Rus, and Kim, K.</font><br>
    <font size="3" style="color:gray;"><u><i>2024 IEEE ICRA Workshop on Wearable</i></u> - <a href="https://sites.google.com/view/icra-2024-wearable-workshop/proceedings"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Poster&Workshop">
  <div class="publication-image">
    <img src="/images/FlipPelt.png" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[w.1] Dual-sided Peltier Elements for Rapid Thermal Feedback in Wearables</b></font><br>
    <font size="3" style="color:dark_gray;">Kang, S., Kim, G., <strong>Hwang, S.</strong>, Park, J., Elsharkawy, A., and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>2024 IEEE ICRA Workshop on Wearable</i></u> - <a href="https://arxiv.org/abs/2405.11807"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Accessibility Conference">
  <div class="publication-image">
    <img src="/images/WatchCap.png" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[c.6] WatchCap: Improving Scanning Efficiency in People with Low Vision through Compensatory Head Movement Stimulation</b></font><br>
    <font size="3" style="color:dark_gray;">Jo, T., Yeo, D., Kim, G., <strong>Hwang, S.</strong>, and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>Proceedings of the ACM on IMWUT</i></u> - <a href="https://dl.acm.org/doi/10.1145/3659592"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Conference FA Award">
  <div class="publication-image">
    <img src="/images/ErgoPulse.gif" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[c.5] ErgoPulse: Electrifying Your Lower Body With Biomechanical Simulation-based Electrical Muscle Stimulation Haptic System in Virtual Reality</b></font><br>
    <font size="3"><strong style="background-color: #ffdd57; padding: 2px 4px; border-radius: 5px;">🏆 Honorable mention</strong></font><br>
    <font size="3" style="color:dark_gray;"><strong>Hwang, S.</strong>, Oh, J., Kang, S., Seong, M., Elsharkawy, A., and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>Proceedings of the 2024 CHI</i></u> - <a href="https://dl.acm.org/doi/10.1145/3613904.3642008"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics AutomotiveUX Conference Award">
  <div class="publication-image">
    <img src="/images/SyncVR.png" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[c.4] SYNC-VR: Synchronizing Your Senses to Conquer Motion Sickness for Enriching In-Vehicle Virtual Reality</b></font><br>
    <font size="3"><strong style="background-color: #ffdd57; padding: 2px 4px; border-radius: 5px;">🏆 Honorable mention</strong></font><br>
    <font size="3" style="color:dark_gray;">Elsharkawy, A., Ataya, A., Yeo, D., An, E., <strong>Hwang, S.</strong>, and Kim, S.</font><br>
		<font size="3" style="color:gray;"><u><i>Proceedings of the 2024 CHI</i></u> - <a href="https://dl.acm.org/doi/10.1145/3613904.3642941"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Locomotion Poster&Workshop">
  <div class="publication-image">
    <img src="/images/GaitWay.gif" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[p.4] GaitWay: Gait Data-Based VR Locomotion Prediction System Robust to Visual Distraction</b></font><br>
    <font size="3" style="color:dark_gray;">Kim, Y., <strong>Hwang, S.</strong>, Oh, J., and Kim, S.</font><br>
		<font size="3" style="color:gray;"><u><i>Extended Abstracts of the 2024 CHI (Late-Breaking Work)</i></u> - <a href="https://dl.acm.org/doi/10.1145/3613905.3651073"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Locomotion AutomotiveUX Poster&Workshop">
  <div class="publication-image">
    <img src="/images/CurvingCar.gif" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[p.3] Curving the Virtual Route: Applying Redirected Steering Gains for Active Locomotion in In-Car VR</b></font><br>
    <font size="3" style="color:dark_gray;">Gim, B., Kang, S., Kim, G, Yeo, D., <strong>Hwang, S.</strong>, and Kim, S.</font><br>
		<font size="3" style="color:gray;"><u><i>Extended Abstracts of the 2024 CHI (Late-Breaking Work)</i></u>  - <a href="https://dl.acm.org/doi/10.1145/3613905.3650746"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Locomotion Journal">
  <div class="publication-image">
    <img src="/images/OLFRDW.jpeg" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[j.2] Evaluation of Visual, Auditory, and Olfactory Stimulus-Based Attractors for Intermittent
     Reorientation in Virtual Reality Locomotion</b></font><br>
    <font size="3" style="color:dark_gray;">Lee, J., <strong>Hwang, S.</strong>, Kim, K., and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>Virtual Reality</i></u> - <a href="https://doi.org/10.1007/s10055-024-00997-y"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Locomotion Journal">
  <div class="publication-image">
    <img src="/images/OptiRDW.jpeg" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[j.1] Effect of Optical Flow and User VR Familiarity on Curvature Gain Thresholds for Redirected Walking</b></font><br>
    <font size="3" style="color:dark_gray;">Lee, J., <strong>Hwang, S.</strong>, Ataya, A., and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>Virtual Reality</i></u> - <a href="https://doi.org/10.1007/s10055-023-00935-4"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Locomotion Conference FA Award">
  <div class="publication-image">
    <img src="/images/BCV_RDW.gif" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[c.3] Enhancing Seamless Walking in Virtual Reality: Application of Bone-Conduction Vibration in Redirected Walking</b></font><br>
    <font size="3"><strong style="background-color: #ffdd57; padding: 2px 4px; border-radius: 5px;">🏆 Honorable mention</strong></font><br>
    <font size="3" style="color:dark_gray;"><strong>Hwang, S.</strong>, Kim, Y., Seo, Y., and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>2023 IEEE International Symposium on Mixed and Augmented Reality (ISMAR)</i></u> - <a href="https://www.computer.org/csdl/proceedings-article/ismar/2023/283800b181/1SBIOSZTWlG"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="AutomotiveUX Conference Award">
  <div class="publication-image">
    <img src="/images/eHMI_AV.png" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[c.2] Designing Virtual Agent Human–Machine Interfaces Depending on the Communication and Anthropomorphism Levels in Augmented Reality</b></font><br>
    <font size="3"><strong style="background-color: #ffdd57; padding: 2px 4px; border-radius: 5px;">🏆 Honorable mention</strong></font><br>
    <font size="3" style="color:dark_gray;">Kang, Y., Choi, S., An, E., <strong>Hwang, S.</strong>, and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>AutomotiveUI 2023</i></u> - <a href="https://dl.acm.org/doi/10.1145/3580585.3606460"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Locomotion Conference FA">
  <div class="publication-image">
    <img src="/images/GVS_BCV_CVS.gif" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[c.1] Electrical, Vibrational, and Cooling Stimuli-Based Redirected Walking: Comparison of Various Vestibular Stimulation-Based Redirected Walking Systems</b></font><br>
    <font size="3" style="color:dark_gray;"><strong>Hwang, S.</strong>, Lee, J., Kim, Y., Seo, Y., and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>Proceedings of the 2023 CHI</i></u> - <a href="https://dl.acm.org/doi/10.1145/3544548.3580862"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Locomotion Poster&Workshop FA">
  <div class="publication-image">
    <img src="/images/VSRDW.gif" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[p.2] REVES: Redirection Enhancement Using Four-Pole Vestibular Electrode Stimulation</b></font><br>
    <font size="3" style="color:dark_gray;"><strong>Hwang, S.</strong>, Lee, J., Kim, Y., and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>Extended Abstracts of the 2022 CHI (Late-Breaking Work)</i></u> - <a href="https://dl.acm.org/doi/10.1145/3491101.3519626"><strong>Link</strong></a></font>
  </div>
</div>

<div class="publication-container" data-tags="Haptics Locomotion Poster&Workshop">
  <div class="publication-image">
    <img src="/images/OLFRDW_LBW.jpeg" alt="Research Image">
  </div>
  <div class="publication-text">
    <font size="4"><b>[p.1] Auditory and Olfactory Stimuli-Based Attractors to Induce Reorientation in Virtual Reality Forward Redirected Walking</b></font><br>
    <font size="3" style="color:dark_gray;">Lee, J., <strong>Hwang, S.</strong>, Kim, K., and Kim, S.</font><br>
    <font size="3" style="color:gray;"><u><i>Extended Abstracts of the 2022 CHI (Late-Breaking Work)</i></u> - <a href="https://dl.acm.org/doi/10.1145/3491101.3519719"><strong>Link</strong></a></font>
  </div>
</div>

<br>
<br>

# Patents & Copyrighted Contents

<div class="publication-text">
<font size="4"><b>[pa.1] Method and System for Supporting Walking in Virtual Environment</b></font><br>
<font size="3" style="color:dark_gray;"><strong>Hwang, S.</strong>, Lee, J., Kim, Y., Seo, Y., and Kim, S.</font><br>
<font size="3" style="color:gray;"><u><i>US Patent App. 18/783,599 || KR Patent App. 10-2023-0,155,898</i></u></font>
</div>

<br>

<div class="publication-text">
<font size="4"><b>[cc.2] Mobility-Linked Virtual Reality-Based Underwater Exploration Immersive Content Game Software (Underwater Exploration & Ocean Trash Collection Game)</b></font><br>
<font size="3" style="color:dark_gray;">Kim, S., Kang, S., Kang, Y., Kim, K., Seong, M., An, E., Yang, H., Yeo, D., Oh, J., Jeon, H., Jo, T., and <strong>Hwang, S.</strong></font><br>
<font size="3" style="color:gray;"><u><i>Copyright for Computer Program Works C-2022-050134</i></u></font>
</div>

<br>

<div class="publication-text">
<font size="4"><b>[cc.1] Mobility-Linked Virtual Reality-Based Underwater Exploration Immersive Content Game Software (Underwater Exploration & Underwater Gem Collection Game)</b></font><br>
<font size="3" style="color:dark_gray;">Kim, S., Kang, S., Kang, Y., Kim, K., Seong, M., An, E., Yang, H., Yeo, D., Oh, J., Jeon, H., Jo, T., and <strong>Hwang, S.</strong></font><br>
<font size="3" style="color:gray;"><u><i>Copyright for Computer Program Works C-2022-050133</i></u></font>
</div>
