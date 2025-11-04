# System Architecture for HandTalk Lokal

## Overview
HandTalk Lokal is an offline-capable hand sign-to-speech translation and learning system for local Filipino dialects. The system uses computer vision and machine learning to recognize Filipino Sign Language (FSL) gestures and convert them into speech in selected local dialects (Ilocano, Hiligaynon, and Maranao).

## System Architecture

```mermaid
graph TD
    A[User Interface Layer] --> B[Gesture Recognition Module]
    A --> C[Learning Module]
    A --> D[Speech Synthesis Module]
    
    subgraph Frontend
        A1[Mobile/Web Application]
        A2[Accessibility Features]
        A3[Dialect Selection]
        A4[Progress Tracker UI]
        A1 --> A2
        A1 --> A3
        A1 --> A4
    end
    
    subgraph Core Processing
        B1[Computer Vision Engine]
        B2[MediaPipe/TensorFlow]
        B3[Gesture Preprocessing]
        B4[Feature Extraction]
        B1 --> B2
        B1 --> B3
        B1 --> B4
        
        C1[Learning Content Management]
        C2[Lesson Modules]
        C3[Interactive Quizzes]
        C4[Video Tutorials]
        C1 --> C2
        C1 --> C3
        C1 --> C4
        
        D1[Text-to-Speech Engine]
        D2[Dialect Voice Models]
        D3[Audio Processing]
        D4[Offline Speech Database]
        D1 --> D2
        D1 --> D3
        D1 --> D4
    end
    
    subgraph Data Layer
        E1[Offline Gesture Dataset]
        E2[Pre-trained ML Models]
        E3[User Progress Data]
        E4[Dialect Vocabulary]
        E1 --> E2
        E2 --> B1
        E3 --> A4
        E4 --> D1
    end
    
    subgraph Hardware
        F1[Camera/Input Device]
        F2[Processing Unit]
        F3[Audio Output]
        F4[Storage]
        F1 --> B1
        F2 --> B1
        F2 --> C1
        F2 --> D1
        F3 --> D1
        F4 --> E1
        F4 --> E2
        F4 --> E3
        F4 --> E4
    end
    
    A --> A1
    A --> A2
    A --> A3
    A --> A4
    B --> B1
    B --> B2
    B --> B3
    B --> B4
    C --> C1
    C --> C2
    C --> C3
    C --> C4
    D --> D1
    D --> D2
    D --> D3
    D --> D4
    B1 --> E1
    C1 --> E3
    D1 --> E4
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