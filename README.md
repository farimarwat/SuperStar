# SuperStar Audio Processing Library

The SuperStar Audio Processing Library is designed to facilitate complex audio processing tasks in Android applications with ease. This powerful interface allows for the application of reverb effects, joining of audio files, trimming of audio clips, and the addition of fun voice transformations such as Minion and Robot effects.

## Key Features

- **Reverb:** Add depth and space to your audio files with a reverb effect.
- **Join:** Seamlessly concatenate two audio files into a single file.
- **Trim:** Extract specific parts of an audio file based on start time and duration.
- **Voice Transformations:** Apply Minion or Robot voice effects to your audio files.
- More effects will come soon

## Getting Started

### Note: Tested only with .wav extensions. Not tested with other formats

### Setup

To utilize the `SuperStar` interface in your project, include the `com.farimarwat.audio.helper` package in your application. Ensure your project is set up with Kotlin support and AndroidX compatibility.

### Implementation
```
implementation 'io.github:farimarwat:superstar:1.0'
```

### Usage

#### Create Instance
```
val superStar = SuperStarBuilder
            .build()
```

#### Apply Reverb
```
 CoroutineScope(Dispatchers.IO).launch {
                superStar.Reverb(
                    source = "/path/to/input.wav", destination = "/path/to/save/output.wav",
                    onComplete = { file ->
                        Log.e(TAG,file.path.toString())
                    },
                    onError = {
                        Log.e(TAG,it.toString())
                    }
                )
            }
```

#### Join two files
```
CoroutineScope(Dispatchers.IO).launch {
    superStar.Join(
        source1 = File("/path/to/input1.wav"), 
        source2 = File("/path/to/input2.wav"), 
        destination = File("/path/to/save/output_joined.wav"),
        onComplete = { file ->
            Log.e(TAG, "Files joined: ${file.path}")
        },
        onError = { exception ->
            Log.e(TAG, exception.toString())
        }
    )
}

```

#### Trim audio file
```
CoroutineScope(Dispatchers.IO).launch {
    superStar.Trim(
        source = File("/path/to/input.wav"), 
        destination = File("/path/to/save/output_trimmed.wav"),
        startTime = "00:00:30", // Example start time
        durationSeconds = 60, // Example duration in seconds
        onComplete = { file ->
            Log.e(TAG, "Audio trimmed: ${file.path}")
        },
        onError = { exception ->
            Log.e(TAG, exception.toString())
        }
    )
}

```

#### Apply Minion sound effect
```
CoroutineScope(Dispatchers.IO).launch {
    superStar.Minion(
        source = File("/path/to/input.wav"), 
        destination = File("/path/to/save/output_minion.wav"),
        onComplete = { file ->
            Log.e(TAG, "Minion voice applied: ${file.path}")
        },
        onError = { exception ->
            Log.e(TAG, exception.toString())
        }
    )
}

```

#### Apply Robot sound effect
```
CoroutineScope(Dispatchers.IO).launch {
    superStar.Robot(
        source = File("/path/to/input.wav"), 
        destination = File("/path/to/save/output_robot.wav"),
        onComplete = { file ->
            Log.e(TAG, "Robot voice applied: ${file.path}")
        },
        onError = { exception ->
            Log.e(TAG, exception.toString())
        }
    )
}

```
