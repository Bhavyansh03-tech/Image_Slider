# Image Slider using HorizontalPager in Jetpack Compose

This repository demonstrates how to create an image slider using the `HorizontalPager` component in Jetpack Compose with Kotlin. The image slider allows users to swipe through a series of images horizontally.

## Features

- **Image Slider**: Swipe through multiple images horizontally.
- **Jetpack Compose**: Built using Jetpack Compose for a modern, declarative UI.
- **Kotlin**: Fully implemented in Kotlin.

## Screenshots

<div style="display: flex; justify-content: center; align-items: center;">
    <img src="https://github.com/Bhavyansh03-tech/Image_Slider/assets/96388594/55f9c7b6-e2af-4432-bda4-7c81a9b7696c" alt="First Screenshot" style="width: 200px; height: auto; margin-right: 10px;">
    <img src="https://github.com/Bhavyansh03-tech/Image_Slider/assets/96388594/a2c93fe6-d29d-4ec9-8164-b10a31b4dabb" alt="Second Screenshot" style="width: 200px; height: auto;">
</div>

## Getting Started

1. Clone the repository:

```bash
git clone https://github.com/Bhavyansh03-tech/Material3_Buttons.git
```

2. Open the project in Android Studio.
3. Build and run the app on your Android device or emulator.


## Implementation

```Kotlin
import androidx.compose.foundation.ExperimentalFoundationApi
import androidx.compose.foundation.Image
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.Box
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.fillMaxWidth
import androidx.compose.foundation.layout.offset
import androidx.compose.foundation.layout.padding
import androidx.compose.foundation.layout.wrapContentHeight
import androidx.compose.foundation.pager.HorizontalPager
import androidx.compose.foundation.pager.PageSize
import androidx.compose.foundation.pager.rememberPagerState
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.automirrored.filled.KeyboardArrowLeft
import androidx.compose.material.icons.automirrored.filled.KeyboardArrowRight
import androidx.compose.material3.Icon
import androidx.compose.material3.IconButton
import androidx.compose.material3.MaterialTheme
import androidx.compose.ui.Modifier
import androidx.compose.ui.draw.clip
import androidx.compose.ui.layout.ContentScale
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.unit.dp
import androidx.compose.runtime.Composable
import androidx.compose.runtime.rememberCoroutineScope
import androidx.compose.ui.Alignment
import kotlinx.coroutines.launch

@OptIn(ExperimentalFoundationApi::class)
@Composable
fun ImageSlider() {

    val photos = listOf(
        R.drawable.img1,
        R.drawable.img2,
        R.drawable.img3,
        R.drawable.img4,
        R.drawable.img5,
    )

    val scope = rememberCoroutineScope()
    val pagerState = rememberPagerState(pageCount = { photos.size })

    Box(
        modifier = Modifier.fillMaxSize()
    ) {
        HorizontalPager(
            state = pagerState,
            pageSize = PageSize.Fill,
            key = { photos[it] }
        ) { index ->
            Image(
                modifier = Modifier.fillMaxSize(),
                painter = painterResource(id = photos[index]),
                contentDescription = null,
                contentScale = ContentScale.Crop
            )
        }
    }

    Box(
        modifier = Modifier
            .fillMaxSize()
            .offset(y = -(19).dp),
        contentAlignment = Alignment.BottomCenter
    ) {
        Box(
            modifier = Modifier
                .offset(y = -(19).dp)
                .fillMaxWidth(0.5f)
                .clip(RoundedCornerShape(100))
                .background(MaterialTheme.colorScheme.background)
                .padding(8.dp)
                .wrapContentHeight()
        ) {
            IconButton(
                onClick = {
                    scope.launch {
                        pagerState.animateScrollToPage(
                            pagerState.currentPage - 1
                        )
                    }
                },
                modifier = Modifier.align(Alignment.CenterStart)
            ) {
                Icon(
                    imageVector = Icons.AutoMirrored.Filled.KeyboardArrowLeft,
                    contentDescription = "Go Back"
                )
            }

            IconButton(
                onClick = {
                    scope.launch {
                        pagerState.animateScrollToPage(
                            pagerState.currentPage + 1
                        )
                    }
                },
                modifier = Modifier.align(Alignment.CenterEnd)
            ) {
                Icon(
                    imageVector = Icons.AutoMirrored.Filled.KeyboardArrowRight,
                    contentDescription = "Go Back"
                )
            }
        }
    }
}
```


## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are greatly appreciated.

1.> Fork the Project.\
2.> Create your Feature Branch `git checkout -b feature/AmazingFeature`.\
3.> Commit your Changes `git commit -m 'Add some AmazingFeature'`.\
4.> Push to the Branch `git push origin feature/AmazingFeature`.\
5.> Open a Pull Request

## Acknowledgements

- Inspiration from various Android development tutorials and documentation.
## Contact

For questions or feedback, please contact [@Bhavyansh03-tech](https://github.com/Bhavyansh03-tech).
