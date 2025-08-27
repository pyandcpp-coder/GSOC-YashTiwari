---
description: Welcome to your team’s developer platform
layout:
  width: wide
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: true
---

# Developer Platform

### GSoC 2025 Final Report: Porting Puara-gestures and Expanding Analysis Capabilities in ossia score

**Student:** Yash Tiwari\
**Organization:** Ossia\
**Mentors:** Edu Meneses, Jean-Michaël Celerier

#### 1. Project Goals

My Google Summer of Code project had two primary objectives. The foundational goal was to port the powerful puara-gestures C++ library to the Avendish framework, making its sophisticated gestural analysis tools available as native processes within the ossia score interactive media environment.

Building on this foundation, the second major goal was to significantly expand the analytical capabilities of ossia score by porting a wide array of advanced analysis and machine learning nodes from the Python-based goofi-pipe project into high-performance C++ processors. The aim was to create a comprehensive, real-time toolkit for artists, musicians, and researchers to perform complex data analysis directly within their creative workflow.

#### 2. What I Accomplished

Over the course of the GSoC program, I successfully completed both primary objectives, delivering a robust and extensive new suite of tools to the ossia score ecosystem. My work can be broken down into two main phases:

**Phase I: Foundational puara-gestures Integration**

I began by porting the core gestural descriptors from the original puara-gestures library. This involved creating stable, efficient, and user-friendly Avendish wrappers for fundamental real-time gesture analysis.

**Successfully Ported Descriptors:**

* **Button:** Detects discrete button-press-like events from continuous data.
* **Jab:** Recognizes fast, directional "jabbing" motions.
* **Roll, Tilt, Shake:** Full porting of orientation and motion descriptors to analyze rotational and accelerometer data.
* **Leaky Integrator:** A crucial utility for smoothing and processing sensor data streams.

**Phase II: Advanced Analysis & Machine Learning Expansion**

This phase focused on dramatically increasing the analytical power of the addon. I systematically ported, and in many cases re-implemented from first principles, a large suite of processors for advanced signal processing and machine learning.

The result is **11 new, high-performance analysis processors**, all of which are now integrated and fully functional within ossia score.

| Processor                         | Description                                                                              | Key Technologies & Skills Demonstrated                                                                                  |
| --------------------------------- | ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Power Band & Power Band EEG**   | Calculates power within specific or standard EEG frequency bands from a PSD.             | xtensor for array processing, C++ algorithm design.                                                                     |
| **Binarize**                      | Converts a continuous signal to a binary (0/1) signal based on a threshold.              | xtensor for efficient, NumPy-like operations.                                                                           |
| **Avalanches**                    | Detects bursts of activity ("avalanches") in a binarized data stream.                    | Stateful algorithm design, C++ performance optimization.                                                                |
| **Correlation**                   | Computes the Pearson correlation and p-value between two signals.                        | Implemented Pearson formula from scratch; integrated **Boost (Math)** for statistical distributions.                    |
| **Tuning Matrix & Reduction**     | Tools for computational music theory; analyzes harmonic relationships in tunings.        | Re-implemented core music theory metrics from scratch, including float-to-fraction conversion.                          |
| **ERP (Event-Related Potential)** | A stateful processor that averages signal segments time-locked to a trigger.             | Complex state management in C++, real-time data buffering.                                                              |
| **VAMP**                          | Finds the "slowest" dynamical components in a time-series using VAMP.                    | Re-implemented core VAMP algorithm using **Eigen** for high-performance linear algebra and eigensolving.                |
| **PCA**                           | Performs Principal Component Analysis to find the primary axes of variance in a dataset. | Re-implemented PCA using **Eigen**, including covariance calculation and eigensolving.                                  |
| **Clustering**                    | Performs KMeans and Agglomerative clustering on N-dimensional data.                      | **Wrote custom, robust KMeans & Agglomerative clustering algorithms from scratch** to solve library instability issues. |
| **Compass & Walker**              | Simulation nodes for creative data generation and transformation.                        | Stateful simulation, C++ algorithm design for geospatial logic.                                                         |

#### 3. Current State of the Project

The project has reached a successful conclusion, meeting and exceeding the initial goals.

* **Functionality:** All implemented processors are fully functional and available in ossia score.
* **Integration:** All contributions have been submitted as separate, reviewed pull requests and have been **merged** into the main score-addon-puara repository.
* **Usability:** Each processor includes user-configurable parameters exposed in the Inspector Panel, allowing for real-time control and experimentation.

#### 4. Future Work & What's Left to Do

While this GSoC project is complete, the foundation I've built opens up many exciting possibilities for future development:

* **Implement the Classifier Node:** The final step would be to implement the full-featured Classifier processor, using mlpack for its robust SVM, RandomForest, and other models. This would complete the core ML suite.
* **Expand Connectivity & Biotuner:** The complex, specialized algorithms in these nodes could be implemented to provide even more advanced biosignal analysis.
* **Performance Profiling:** A dedicated performance analysis could identify bottlenecks and lead to further optimizations, especially for the iterative ML algorithms.
* **VST/LV2 Plugin Exploration:** As outlined in the original proposal, these Avendish processors could be compiled into standard audio plugins, dramatically expanding their reach to musicians and producers in DAWs.

#### 5. Merged Contributions (Pull Requests)

All of my work was submitted through a series of 15+ pull requests, all of which have been successfully merged into the ossia/score-addon-puara master branch.

* [#29: feat(analysis): Add Power Band EEG processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F29)
* [#26: feat(puara): Add PCAAvnd processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F26)
* [#24: Feat: Adding Clustering Feature Custom](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F24)
* [#22: feat(simulation): Add Walker processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F22)
* [#21: feat(analysis): Add ERP processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F21)
* [#20: feat(analysis): Add Compass processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F20)
* [#19: feat(analysis): Add Binarize processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F19)
* [#18: feat(analysis): Add Avalanches processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F18)
* [#17: feat(analysis): Add VAMP processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F17)
* [#15: feat(analysis): Add Correlation processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F15)
* [#13: feat(analysis): Add Power Band processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F13)
* [#9: feat: Add Puara Button gesture processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F9)
* [#7: feat: Add Puara Leaky Integrator processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F7)
* [#6: feat: Add Puara Roll gesture processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F6)
* [#5: Add Puara Tilt gesture processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F5)
* [#3: Add Puara Shake gesture processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F3)
* [#2: feat: Add Puara Jab gesture processor](https://www.google.com/url?sa=E\&q=https%3A%2F%2Fgithub.com%2Fossia%2Fscore-addon-puara%2Fpull%2F2)

#### 6. Challenges & Key Learnings

This project was a fantastic learning experience that presented several interesting challenges:

* **Technical Challenge: Library Instability:** My biggest technical hurdle was the instability of the dlib library in the macOS build environment, which caused crashes in fundamental functions like KMeans. Instead of being blocked, I took this as an opportunity to deepen my understanding of the algorithms. I successfully **implemented both KMeans and Agglomerative Clustering algorithms from scratch**, resulting in a custom, robust, and dependency-free solution that is now merged and working reliably.
* **Learning: Deep Dive into Modern C++ for Real-Time Systems:** This project forced me to move beyond textbook C++ into the practical realities of high-performance code. I learned to use libraries like **Eigen** for optimized linear algebra and **xtensor** for array programming, and gained critical experience in managing the state of complex, real-time processors in a memory-safe way.
* **Learning: Re-implementing, Not Just Porting:** I quickly learned that "porting" from Python to C++ is not a direct translation. To achieve the necessary performance, I had to re-implement the core mathematical logic of algorithms like PCA, VAMP, and the tuning metrics from first principles using efficient C++ libraries. This was incredibly rewarding and solidified my understanding of the underlying data science.
* **Learning: Professional Open-Source Workflow:** Contributing to a mature project like ossia score taught me the importance of a clean, professional workflow. I learned how to structure contributions into atomic commits and pull requests, how to write clear documentation and testing instructions, and how to effectively integrate feedback from my mentors. This experience was just as valuable as the technical work itself.
