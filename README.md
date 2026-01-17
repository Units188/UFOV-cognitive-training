# Cognitive Training - Multi-Task System

## Description

Web-based cognitive training system based on **UFOV (Useful Field of View)** training methodology. Features 4 progressive adaptive levels designed to assess and improve visual attention, spatial localization, and multi-sensory processing abilities. The system automatically adjusts difficulty based on real-time performance evaluation.

## Features

### Screen Calibration
- Screen calibration at startup to ensure accurate physical dimensions
- Adaptation to different screen resolutions

### Level Progression

**Level 1: Central Identification**
- Identification of an object briefly displayed at screen center
- Duration: 5 minutes maximum
- Adaptive presentation time based on performance

**Level 2: Dual Identification**
- Identification of central object + peripheral object
- Introduction of peripheral vision
- Duration: 5 minutes maximum

**Level 3: Identification and Localization**
- Central and peripheral identification
- Spatial localization (click on position)
- Addition of visual distractors
- Duration: 5 minutes maximum

**Level 4: Triple Task**
- All previous tasks
- Identification of auditory stimulus (low/high pitch)
- Maximum difficulty level
- Duration: 5 minutes maximum

## Difficulty Adaptation

The system uses an adaptive algorithm that:
- Adjusts stimulus presentation time based on performance
- Evaluates every 5 trials with a 75% success threshold
- Decreases display time when performance is good
- Increases display time when performance is insufficient

## Data Collection

### Data Format
See `Notice.txt` for detailed data formats per task.

**Common Information:**
- Participant ID
- Session ID
- Trial number
- Presentation time
- Response time
- Success rate
- Elapsed time since start

**Level-specific data:**
- Levels 2-4: Target distance from center (pixels)
- Levels 3-4: Click distance from target (pixels)
- Level 4: Sound type and identification success

## Technologies Used

- HTML5
- CSS3
- JavaScript (Vanilla)
- Web Audio API (for auditory stimuli)
- JATOS (for experiment management)

## Installation

### Using with JATOS

1. Download and install JATOS: https://www.jatos.org/
2. Import HTML files into JATOS
3. Configure component order:
   - index.html (welcome and calibration)
   - task1.html
   - task2.html
   - task3.html
   - task4.html
   - end.html (final questionnaires)

### Standalone Usage (without JATOS)

**Note:** Some features require JATOS (data recording, task navigation).

## Recommended Usage Conditions

- **Distance**: Maximum 40 cm from screen
- **Environment**: Quiet, distraction-free
- **Hardware**: Mouse recommended (rather than trackpad)
- **Display Mode**: Fullscreen recommended
- **Audio**: Speakers or headphones enabled (level 4)

## Project Structure

```
.
├── index.html          # Welcome page and calibration
├── task1.html          # Level 1 - Central identification
├── task2.html          # Level 2 - Dual identification
├── task3.html          # Level 3 - Identification + localization
├── task4.html          # Level 4 - Triple task
├── end.html            # Final questionnaires (RSME, self-assessment)
├── Notice.txt          # Data format documentation
└── README.md           # This file
```

## Customization

### Adaptive Parameters

Modify constants in each task*.html file:

```javascript
const adaptiveConfig = {
    trialsBeforeAdjustment: 5,    // Number of trials before adjustment
    successThreshold: 0.75,        // Success threshold (75%)
    timeMultiplier: {
        increase: 1.2,             // Time increase factor
        decrease: 0.8              // Time decrease factor
    },
    timeConstraints: {
        min: 10,                   // Minimum time (ms)
        max: 2000,                 // Maximum time (ms)
        initial: 500               // Initial time (ms)
    }
};
```

### Level Progression Thresholds

Modify the `threshold` constant in each file to adjust the threshold for advancing to the next level:

- Task 1: 12 ms
- Task 2: 25 ms
- Task 3: 100 ms
- Task 4: 250 ms

## Authors

Units188

## License

[To be defined]

## Citation

If you use this system in your research, please cite:

```
[To be completed with appropriate citation information]
```

## Contact

GitHub: @Units188
