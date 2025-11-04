# System Architecture for HandTalk Lokal

## Overview
HandTalk Lokal is an offline-capable hand sign-to-speech translation and learning system for local Filipino dialects. The system uses computer vision and machine learning to recognize Filipino Sign Language (FSL) gestures and convert them into speech in selected local dialects (Ilocano, Hiligaynon, and Maranao).

## System Architecture

```mermaid
graph LR
    %% Main System Components %%
    subgraph "USER INTERFACE LAYER"
        A1[Mobile/Web Application] --> A2[Accessibility Features]
        A1 --> A3[Dialect Selection]
        A1 --> A4[Progress Tracker UI]
    end

    subgraph "CORE PROCESSING MODULES"
        subgraph "GESTURE RECOGNITION MODULE"
            B1[Computer Vision Engine] --> B2[MediaPipe/TensorFlow]
            B1 --> B3[Gesture Preprocessing]
            B1 --> B4[Feature Extraction]
        end

        subgraph "LEARNING MODULE"
            C1[Learning Content Management] --> C2[Lesson Modules]
            C1 --> C3[Interactive Quizzes]
            C1 --> C4[Video Tutorials]
        end

        subgraph "SPEECH SYNTHESIS MODULE"
            D1[Text-to-Speech Engine] --> D2[Dialect Voice Models]
            D1 --> D3[Audio Processing]
            D1 --> D4[Offline Speech Database]
        end
    end

    subgraph "DATA LAYER"
        E1[Offline Gesture Dataset] --> E2[Pre-trained ML Models]
        E2 -->|"Model Data"| B1
        E3[User Progress Data] -->|"Progress"| A4
        E4[Dialect Vocabulary] -->|"Vocabulary"| D1
    end

    subgraph "HARDWARE COMPONENTS"
        F1[Camera/Input Device] -->|"Video Input"| B1
        F2[Processing Unit] -->|"Processing"| B1
        F2 -->|"Processing"| C1
        F2 -->|"Processing"| D1
        F3[Audio Output] -->|"Audio"| D1
        F4[Storage] -->|"Storage"| E1
        F4 -->|"Storage"| E2
        F4 -->|"Storage"| E3
        F4 -->|"Storage"| E4
    end

    %% Data Flows %%
    A1 -- "User Input" --> B1
    A1 -- "Navigation" --> C1
    A1 -- "Voice Output Request" --> D1
    B1 -- "Recognized Gestures" --> D1
    C1 -- "Learning Data" --> E3
    D1 -- "Speech Output" --> F3
    E1 -- "Training Data" --> E2
    E2 -- "ML Models" --> B1
    E3 -- "Progress Data" --> A4
    E4 -- "Voice Data" --> D1

    style A1 fill:#e1f5fe
    style B1 fill:#f3e5f5
    style C1 fill:#e8f5e8
    style D1 fill:#fff3e0
    style E1 fill:#fce4ec
    style F1 fill:#f1f8e9
```

## Component Descriptions

### User Interface Layer
- **Mobile/Web Application**: Primary interface for users to interact with the system
- **Accessibility Features**: Large buttons, clear visuals, and voice guidance for users with disabilities
- **Dialect Selection**: Allows users to choose their preferred local dialect (Ilocano, Hiligaynon, or Maranao)
- **Progress Tracker UI**: Visual representation of user learning achievements and improvements

### Gesture Recognition Module
- **Computer Vision Engine**: Core engine responsible for processing visual input
- **MediaPipe/TensorFlow**: Frameworks used for real-time gesture recognition
- **Gesture Preprocessing**: Initial processing of raw camera input
- **Feature Extraction**: Identification of key features from gestures for recognition

### Learning Module
- **Learning Content Management**: System for organizing and delivering educational content
- **Lesson Modules**: Structured learning content for teaching sign language
- **Interactive Quizzes**: Assessment tools to test user knowledge
- **Video Tutorials**: Visual demonstrations of sign language gestures

### Speech Synthesis Module
- **Text-to-Speech Engine**: Converts recognized gestures into audible speech
- **Dialect Voice Models**: Specific voice models for each supported dialect
- **Audio Processing**: Handles audio output quality and clarity
- **Offline Speech Database**: Pre-loaded database of speech samples for offline operation

### Data Layer
- **Offline Gesture Dataset**: Collection of labeled gesture images for recognition
- **Pre-trained ML Models**: Machine learning models trained on the gesture dataset
- **User Progress Data**: Storage of user learning achievements and statistics
- **Dialect Vocabulary**: Collection of words and phrases in each supported dialect

### Hardware
- **Camera/Input Device**: Captures user hand gestures for recognition
- **Processing Unit**: Device responsible for running the application
- **Audio Output**: Speakers or headphones for speech output
- **Storage**: Local storage for offline datasets, models, and user data

## Data Flow
1. User interacts with the Mobile/Web Application
2. Camera captures hand gestures
3. Computer Vision Engine processes gestures using MediaPipe/TensorFlow
4. Recognized gestures are matched against the Offline Gesture Dataset
5. Corresponding text is retrieved from the Dialect Vocabulary
6. Text-to-Speech Engine converts text to speech using Dialect Voice Models
7. Audio is output through Audio Output devices
8. User interactions and progress are stored in User Progress Data
9. Learning Module provides educational content and assessments

## Offline Capabilities
All core components are designed to function without internet connectivity:
- Pre-trained models are stored locally
- Speech databases are pre-loaded
- User data is stored locally
- Learning content is bundled with the application
