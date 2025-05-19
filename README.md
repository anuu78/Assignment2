# Assignment 2 Android App – NIT3213

This Android application was developed as part of **Assignment 2** for the NIT3213 unit at Victoria University.
The app demonstrates secure login, dashboard data display, and detail viewing by integrating with the public VU API service. It use modern Android development best practices including MVVM, Retrofit, Hilt, and ViewBinding.



## 1. Features

1.1 Login Screen
- Authenticates users using their first name and student ID (e.g., `s12345678`).
- Uses location-based login endpoints (`/footscray/auth`, `/sydney/auth`, `/ort/auth`).

1.2 Dashboard Screen
- Displays a list of travel destinations from the API using the `keypass`.
- Uses a RecyclerView for clean and scrollable data display.

1.3 Details Screen
- Shows detailed information about a destination, including long descriptions.

1.4 Logout
- Lets users return to the login screen from the details screen.



## 2. Architecture

- MVVM (Model-View-ViewModel): Clean separation of UI and logic
- Hilt: Dependency Injection
- Retrofit: For HTTP requests
- Gson: For JSON parsing
- LiveData + ViewModel: Reactive UI updates
- ViewBinding: Type-safe view access in Kotlin



## 3. Project Structure

com.example.vuapp
├── data
│ ├── api
│ │ ├── AuthApiService.kt
│ │ └── DashboardApiService.kt
│ ├── model
│ │ ├── DashboardResponse.kt
│ │ └── Entity.kt
│ └── repository
│ ├── AuthRepository.kt
│ └── DashboardRepository.kt
│
├── di
│ └── AppModule.kt
│
├── ui
│ ├── login
│ │ ├── LoginActivity.kt
│ │ └── LoginViewModel.kt
│ ├── dashboard
│ │ ├── DashboardActivity.kt
│ │ ├── DashboardViewModel.kt
│ │ └── EntityAdapter.kt
│ └── details
│ └── DetailsActivity.kt
│
├── utils
│ └── Constants.kt
│
├── MainActivity.kt
└── MainApplication.kt


## 4. Dependencies

kotlin
// Retrofit
implementation("com.squareup.retrofit2:retrofit:2.9.0")
implementation("com.squareup.retrofit2:converter-gson:2.9.0")

// Hilt for DI
implementation("com.google.dagger:hilt-android:2.50")
kapt("com.google.dagger:hilt-compiler:2.50")

// ViewModel & LiveData
implementation("androidx.lifecycle:lifecycle-viewmodel-ktx:2.6.2")
implementation("androidx.lifecycle:lifecycle-livedata-ktx:2.6.2")

// Material UI
implementation("com.google.android.material:material:1.11.0")

// ViewBinding
buildFeatures {
viewBinding = true
}

## 5. API Endpoints
Base URL: https://nit3213api.onrender.com/

Endpoint Method Description
/footscray/auth POST Login (based on location)
/dashboard/{keypass} GET Retrieve destination entities list

## 6. UI/UX
1.Follows modern Material Design principles

2.Scrollable layouts for long content

3.Displays error messages for:

i.Missing login fields

ii.Invalid credentials

iii.API failures

4.Includes logout and back navigation

5.Responsive and accessible on emulator and device

## 7. Testing
1.Tested on emulator.

2.Verified:

i.Successful and failed login

ii.API loading delays

iii.Navigation and logout

3.Optional unit tests available for ViewModel logic

## 8. How to Use the App
1.Open the project in Android Studio.

2.Connect a physical Android device or emulator.

3.Run the app.

4.On the login screen, enter:

I.Username: Your first name

II.Password: Your student ID (e.g., s12345678)

III.If successful, you will see the list of destinations.

5.Click any item to view its full details.

6.Press Logout to return to the login screen.

## 9. License
This project was developed for academic purposes as part of the NIT3213 course at Victoria University and
Use is limited to educational demonstrations and assessments.

## 10. Author
Student Name: Sagya Gurung
Student ID: s8135804
