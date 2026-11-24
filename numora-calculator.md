# Portfolio Project Data — Numora - Calculator

- **Category:** `desktop-mobile` (`Mobile App`)
- **Category Label:** `Mobile App`
- **Accent Color:** `amber`
- **Target Assets Folder:** `public/images/projects/numora_calculator/`
- **Required Local Images:** `banner.webp`, `image01.webp`

## TypeScript Data (`ProjectCaseStudy`)

```typescript
{
  "id": "numora-calculator",
  "code": "PRO-09 // APP-05",
  "title": "Numora - Calculator",
  "category": "desktop-mobile",
  "categoryLabel": "Mobile App",
  "year": "2022",
  "status": "Completed",
  "accentColor": "amber",
  "repoUrl": "https://github.com/weztcy/Numora-Calculator",
  "license": "MIT License",
  "banner": "/images/projects/numora_calculator/banner.webp",
  "summary": "A native Android scientific calculator built with Kotlin, Jetpack Compose, and a custom recursive-descent expression parser.",
  "projectDescription": "Numora - Calculator is a native Android application crafted with Kotlin and Jetpack Compose on an AMOLED dark theme. Powered by a custom lexer, recursive-descent expression parser, and BigDecimal formatter, it evaluates standard arithmetic and scientific math accurately offline.",
  "architectureSummary": "Unidirectional Compose MVVM pipeline connecting CalculatorScreen and CalculatorViewModel to a pure-Kotlin Lexer, recursive-descent ExpressionParser, and BigDecimal NumberFormatter.",
  "techStack": [
    "Kotlin",
    "Jetpack Compose",
    "Material Design",
    "Android SDK",
    "Kotlin Coroutines",
    "Android ViewModel",
    "JUnit",
    "Gradle"
  ],
  "telemetryMatrix": {
    "projectType": "Native Android Mobile App",
    "targetPlatform": "Android 8.0+ (API 26 to 37)",
    "primaryDomain": "Scientific & Arithmetic Computation",
    "architecturePipeline": "MVVM + Recursive Descent Parser",
    "testingAndAudit": "JUnit 4 Unit Test Suite",
    "projectStatus": "Completed",
    "projectYear": "2022"
  },
  "desktopMobileProjectInfo": {
    "applicationType": "Native Android Mobile Application",
    "targetPlatform": "Android (API 26+)",
    "developmentStatus": "Completed",
    "developmentYear": "2022",
    "applicationCategory": "Scientific & Utility Calculator"
  },
  "desktopMobileBackground": "Mobile calculators often rely on external evaluators or sequential input models that mishandle operator precedence and implicit multiplication. Students and technical users need reliable parenthesized evaluation, DEG/RAD angle switching, and responsive visual feedback inside an uncluttered AMOLED dark interface.",
  "desktopMobileProblemStatements": [
    {
      "title": "Precedence & Implicit Multiplication Gaps",
      "description": "Naive sequential evaluators process operators left-to-right without respecting mathematical precedence, right-associative exponentiation, or implicit products such as 2π and 2(5).",
      "issueCode": "ISSUE_01"
    },
    {
      "title": "Opaque Floating-Point Artifacts & Errors",
      "description": "Raw IEEE-754 double outputs expose precision noise such as -0.0 or trailing zeros, while invalid domains like division by zero or negative square roots lack structured error feedback.",
      "issueCode": "ISSUE_02"
    },
    {
      "title": "Cluttered Scientific Keypad Layouts",
      "description": "Exposing all trigonometric, factorial, and constant keys simultaneously crowds small mobile viewports during everyday arithmetic tasks.",
      "issueCode": "ISSUE_03"
    }
  ],
  "desktopMobileObjectives": [
    {
      "title": "Deterministic Pure-Kotlin Expression Engine",
      "description": "Implement a standalone Lexer and recursive-descent ExpressionParser handling parentheses, unary negation, right-associative powers, factorials, percentages, and implicit multiplication without external dependencies.",
      "targetTag": "TARGET_01"
    },
    {
      "title": "Precision Numeric Formatting & Domain Safety",
      "description": "Normalize outputs using BigDecimal HALF_UP rounding up to 12 decimal places, switch cleanly to scientific notation at extreme scales, and surface explicit CalculationResult.Error messages.",
      "targetTag": "TARGET_02"
    },
    {
      "title": "Adaptive Dual-Mode Jetpack Compose UI",
      "description": "Deliver an AMOLED black Material 3 interface with animated Standard/Scientific mode toggling, DEG/RAD angle switching, haptic feedback, and dynamic text scaling.",
      "targetTag": "TARGET_03"
    }
  ],
  "desktopMobileFeatures": [
    {
      "title": "Standard & Scientific Keypad Modes",
      "description": "Switch dynamically between a clean 4x4 basic keypad and an expanded scientific layout via AnimatedVisibility with expandVertically and shrinkVertically transitions.",
      "badge": "Dual Mode"
    },
    {
      "title": "Recursive-Descent Math Parser",
      "description": "Evaluates nested parentheses, operator precedence, unary minus, right-associative power (2^3^2), postfix factorial up to 170!, percentage, and implicit multiplication.",
      "badge": "Math Engine"
    },
    {
      "title": "Trigonometric, Logarithmic & Constant Support",
      "description": "Supports sin, cos, tan, asin, acos, atan, log, ln, sqrt, plus π and e constants with real-time DEG/RAD angle conversion.",
      "badge": "Scientific"
    },
    {
      "title": "BigDecimal Output Normalization",
      "description": "Eliminates near-zero noise below 1e-12, strips trailing decimal zeros, and formats magnitudes outside [1e-10, 1e12) in scientific notation.",
      "badge": "Precision"
    },
    {
      "title": "Tactile AMOLED Dark Design System",
      "description": "Uses pure #000000 AMOLED background, color-coded button categories, spring press-scale animation (0.92f), and KEYBOARD_TAP haptic feedback.",
      "badge": "Material 3"
    }
  ],
  "desktopMobileInterfaceShowcase": [
    {
      "imageUrl": "/images/projects/numora_calculator/image01.webp"
    }
  ],
  "desktopMobileUserFlow": {
    "summary": "Users interact with a reactive single-screen interface where keypad taps dispatch sealed actions to the ViewModel. Expressions update live in the display card, Scientific Mode expands extra function rows with smooth vertical animation, and pressing equals evaluates and formats the final output.",
    "steps": [
      {
        "step": "01",
        "title": "Input Composition & Mode Selection",
        "description": "User taps digits, operators, or toggles SCI/STD and DEG/RAD controls; CalculatorKeypad dispatches sealed CalculatorAction events with haptic tap feedback.",
        "actorOrNode": "User / Compose UI"
      },
      {
        "step": "02",
        "title": "Unidirectional State Update",
        "description": "CalculatorViewModel processes the action, updates expression or mode flags inside MutableStateFlow<CalculatorUiState>, and clears stale error states.",
        "actorOrNode": "CalculatorViewModel"
      },
      {
        "step": "03",
        "title": "Lexical & Syntactic Evaluation",
        "description": "On Calculate, CalculatorEngine invokes Lexer to tokenize the expression string and ExpressionParser to evaluate the AST precedence rules under the active AngleMode.",
        "actorOrNode": "CalculatorEngine"
      },
      {
        "step": "04",
        "title": "Formatting & Animated Display",
        "description": "NumberFormatter normalizes the Double output via BigDecimal and returns CalculationResult.Success or Error, triggering AnimatedContent fade transitions in CalculatorDisplay.",
        "actorOrNode": "NumberFormatter / UI"
      }
    ]
  },
  "desktopMobileArchitecture": {
    "summary": "The application follows a unidirectional MVVM architecture in Kotlin. Jetpack Compose UI components observe an immutable StateFlow from CalculatorViewModel, which routes user actions to a pure-Kotlin CalculatorEngine pipeline composed of a Lexer, recursive-descent ExpressionParser, and BigDecimal NumberFormatter.",
    "layers": [
      {
        "name": "Presentation Layer",
        "role": "Renders AMOLED Material 3 display and keypad composables, handles window system bar styling, haptic feedback, and animations.",
        "tech": "Jetpack Compose",
        "components": [
          "MainActivity",
          "CalculatorScreen",
          "CalculatorDisplay",
          "CalculatorKeypad",
          "CalculatorButton"
        ]
      },
      {
        "name": "State & Domain Model Layer",
        "role": "Manages unidirectional action dispatch and exposes immutable UI state streams for expression, result, error, and mode flags.",
        "tech": "Android ViewModel",
        "components": [
          "CalculatorViewModel",
          "CalculatorUiState",
          "CalculatorAction",
          "AngleMode",
          "CalculatorOperator",
          "ScientificFunction"
        ]
      },
      {
        "name": "Calculation Engine Layer",
        "role": "Performs lexical tokenization, recursive-descent grammar evaluation, domain validation, and precision number formatting.",
        "tech": "Kotlin",
        "components": [
          "CalculatorEngine",
          "Lexer",
          "ExpressionParser",
          "NumberFormatter",
          "Token",
          "CalculationResult"
        ]
      }
    ]
  },
  "desktopMobileDataManagement": {
    "storageType": "In-Memory StateFlow",
    "stateEngine": "AndroidX ViewModel with MutableStateFlow",
    "offlineSyncStrategy": "Fully offline local computation with zero network dependencies",
    "cachingMechanism": "Ephemeral reactive UI state held in ViewModel across configuration lifecycle"
  },
  "desktopMobilePlatformImplementation": [
    {
      "title": "System Bars & Window Insets Control",
      "description": "MainActivity configures WindowCompat.setDecorFitsSystemWindows(window, true), enforces pure black status and navigation bars, disables Android navigation bar contrast scrims, and applies statusBarsPadding, navigationBarsPadding, and imePadding.",
      "badge": "Android Window"
    },
    {
      "title": "Native Haptic & Spring Press Feedback",
      "description": "CalculatorButton triggers HapticFeedbackConstants.KEYBOARD_TAP via LocalView on every key press alongside a spring-interpolated scale animation and Material elevation transition.",
      "badge": "Haptics & UI"
    },
    {
      "title": "Android Gradle Packaging & Keep Rules",
      "description": "Configured with Android Gradle Plugin, Gradle Version Catalog, Java 11 bytecode compatibility, minSdk 26 / targetSdk 37 bounds, and custom keepRules/rules.keep metadata.",
      "badge": "Android Build"
    }
  ],
  "desktopMobileTechSpecs": {
    "programmingLanguage": "Kotlin",
    "framework": "Jetpack Compose",
    "localStorage": "In-Memory StateFlow"
  },
  "desktopMobilePlatformSpecs": {
    "targetPlatform": "Android Mobile Devices",
    "packageFormat": "Android APK and AAB",
    "targetArchitecture": "ARM64 and x86-64",
    "buildFootprint": "Lightweight Native Compose Build"
  }
}
```
