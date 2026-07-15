# Getting Started

<cite>
**Referenced Files in This Document**
- [index.html](file://index.html)
</cite>

## Table of Contents
1. [Introduction](#introduction)
2. [Quick Start](#quick-start)
3. [Browser Requirements](#browser-requirements)
4. [First-Time Setup](#first-time-setup)
5. [Dashboard Overview](#dashboard-overview)
6. [Adding Food Entries](#adding-food-entries)
7. [Understanding Preset Foods](#understanding-preset-foods)
8. [Manual Food Entry](#manual-food-entry)
9. [Managing Your Food Diary](#managing-your-food-diary)
10. [Mobile Usage Guide](#mobile-usage-guide)
11. [Troubleshooting Common Issues](#troubleshooting-common-issues)
12. [Best Practices](#best-practices)

## Introduction

NutriTrack is a lightweight, browser-based nutrition tracking application designed to help you monitor your daily caloric intake and macronutrient consumption. Built as a single HTML file, it requires no installation or server setup - simply open it in any modern web browser to start tracking your nutrition immediately.

The application features:
- Real-time calorie and macronutrient tracking
- Pre-loaded Thai food database for quick logging
- Intuitive dashboard with visual progress indicators
- Persistent data storage using browser localStorage
- Mobile-responsive design for on-the-go tracking

## Quick Start

Getting started with NutriTrack is incredibly simple:

1. **Open the application**: Double-click the `index.html` file to launch it in your default web browser
2. **Set your goals**: Configure your daily nutritional targets (calories, protein, carbs, fats)
3. **Start logging**: Use preset foods or manually enter custom items
4. **Monitor progress**: Watch your real-time progress updates on the dashboard

That's it! No registration, no downloads, no complex setup required.

## Browser Requirements

NutriTrack works with all modern web browsers and devices:

### Supported Browsers
- **Chrome** (version 80+)
- **Firefox** (version 75+)
- **Safari** (version 13+)
- **Edge** (version 80+)
- **Opera** (version 67+)

### Device Compatibility
- **Desktop computers** (Windows, macOS, Linux)
- **Tablets** (iPad, Android tablets)
- **Smartphones** (iPhone, Android phones)

### Technical Requirements
- JavaScript enabled
- localStorage access permissions
- Modern CSS support (flexbox, grid, gradients)
- Responsive viewport support

## First-Time Setup

When you first open NutriTrack, you'll see the default dashboard with pre-configured nutritional goals. Here's how to customize them for your needs:

### Understanding Default Goals
The application starts with these default daily targets:
- **Calories**: 1,800 kcal
- **Protein**: 120g
- **Carbohydrates**: 150g  
- **Fats**: 50g

### Customizing Your Goals
To modify your nutritional targets:

1. **Access the goal configuration**: Look for the settings area in the header section
2. **Adjust calorie target**: Set your daily caloric goal based on your weight management objectives
3. **Configure macronutrients**: Adjust protein, carbohydrate, and fat targets according to your dietary preferences
4. **Save changes**: Your new goals will be automatically saved to your browser's storage

### Goal Setting Tips
- **Weight loss**: Set calories below your maintenance level (typically 1,500-1,800 kcal)
- **Muscle building**: Increase protein intake (1.6-2.2g per kg body weight)
- **Balanced diet**: Follow the 40/30/30 macro split (carbs/protein/fats)

## Dashboard Overview

The NutriTrack dashboard provides a comprehensive view of your daily nutrition progress through several key components:

### Calorie Progress Ring
Located at the top-left of the dashboard, this circular progress indicator shows:
- **Current intake**: Total calories consumed today
- **Remaining allowance**: Calories left to reach your goal
- **Overage display**: Shows excess calories if you've exceeded your target
- **Visual feedback**: Color changes when you exceed your calorie limit

### Macronutrient Tracker
The right panel displays detailed breakdown of your macronutrient intake:
- **Protein tracker**: Blue progress bar showing protein consumption vs. goal
- **Carbohydrate tracker**: Amber progress bar for carb intake monitoring
- **Fat tracker**: Pink progress bar for fat consumption tracking
- **Percentage badges**: Show completion percentage for each macronutrient

### Real-Time Updates
All dashboard elements update instantly as you add food entries, providing immediate feedback on your nutritional progress.

## Adding Food Entries

NutriTrack offers two convenient methods for logging your meals: preset quick-add and manual form entry.

### Method 1: Preset Quick-Add

The preset system provides one-click logging for common Thai foods:

1. **Select meal category**: Choose from breakfast, lunch, dinner, or snack using the dropdown menu
2. **Browse preset foods**: Scroll through the grid of popular Thai dishes
3. **Tap to add**: Click any preset food item to instantly log it to your selected meal
4. **View confirmation**: A toast notification confirms successful addition

#### Available Preset Foods
The application includes these nutritious options:
- 🍗 Chicken breast (120 kcal, 25g protein)
- 🍚 Chicken rice (600 kcal, 20g protein)
- 🥚 Boiled egg (75 kcal, 7g protein)
- 🥤 Protein shake (120 kcal, 25g protein)
- 🍖 Sticky rice with grilled pork (400 kcal, 15g protein)
- 🥗 Green papaya salad (150 kcal, 5g protein)
- 🍜 Tom yum noodle soup (350 kcal, 15g protein)
- 🍌 Banana (105 kcal, 1g protein)

### Method 2: Manual Form Entry

For custom foods not in the preset list:

1. **Navigate to the form**: Scroll down to the "Add Food Entry" section
2. **Fill in food details**:
   - **Food name**: Enter the name of your food item
   - **Calories**: Input total caloric content
   - **Meal category**: Select appropriate meal time
   - **Macronutrients**: Enter protein, carbohydrates, and fat amounts
3. **Submit entry**: Click the "Record Food" button
4. **Confirmation**: Receive toast notification and see immediate dashboard updates

## Understanding Preset Foods

The preset food system is designed for quick logging of commonly consumed Thai dishes. Each preset includes complete nutritional information:

### Preset Food Structure
Each preset contains:
- **Name**: Display name of the food item
- **Calories**: Total energy content in kilocalories
- **Protein**: Grams of protein content
- **Carbohydrates**: Grams of carbohydrate content
- **Fats**: Grams of fat content
- **Emoji icon**: Visual identifier for quick recognition

### How Presets Work
1. **Selection**: Choose your desired meal category from the dropdown
2. **Addition**: Click any preset food button
3. **Automatic logging**: The food is instantly added to your selected meal
4. **Real-time updates**: Dashboard reflects changes immediately

### Customizing Preset Selection
You can change which meal category receives preset additions by selecting from:
- 🌅 Breakfast (มื้อเช้า)
- ☀️ Lunch (มื้อกลางวัน) 
- 🌙 Dinner (มื้อเย็น)
- 🍪 Snack (ของว่าง)

## Manual Food Entry

The manual entry form provides complete flexibility for logging any food item:

### Form Fields Explained

#### Basic Information
- **Food Name**: Descriptive name of your food item (required)
- **Calories**: Total caloric content in kcal (required, minimum 0)
- **Meal Category**: Dropdown selection for meal timing

#### Macronutrient Breakdown
- **Protein (g)**: Grams of protein content (required, supports decimals)
- **Carbohydrates (g)**: Grams of carbohydrate content (required, supports decimals)
- **Fats (g)**: Grams of fat content (required, supports decimals)

### Form Validation
The form includes built-in validation:
- All fields are required before submission
- Numeric values must be non-negative
- Decimal precision supported for accurate macro tracking
- Empty food names are rejected

### Best Practices for Manual Entry
- **Be consistent**: Use standardized food names for easier tracking
- **Estimate accurately**: Use nutrition labels or reliable databases for portion sizes
- **Log immediately**: Record foods as soon as possible after eating
- **Include condiments**: Don't forget sauces, oils, and cooking ingredients

## Managing Your Food Diary

Your food diary organizes all logged entries by meal category with detailed nutritional information:

### Meal Categories
The diary is divided into four main sections:
- **Breakfast**: Morning meals and snacks
- **Lunch**: Midday meals and snacks
- **Dinner**: Evening meals and snacks
- **Snack**: Between-meal snacks throughout the day

### Individual Food Items
Each food entry displays:
- **Food name**: Clear identification of the item
- **Caloric content**: Rounded calorie count
- **Macro breakdown**: Protein (blue), Carbohydrates (amber), Fats (pink)
- **Timestamp**: Time of entry for reference
- **Delete option**: Hover to reveal delete button

### Meal Totals
Each meal section shows:
- **Total calories**: Sum of all items in that meal category
- **Visual indicators**: Color-coded headers for easy identification
- **Empty state messaging**: Helpful prompts when no items are logged

### Deleting Food Entries
To remove an incorrect entry:
1. **Hover over the food item**: The delete button appears on the right side
2. **Click delete**: Remove the specific food entry
3. **Confirmation**: Toast notification confirms deletion
4. **Automatic recalculation**: Dashboard and totals update immediately

### Data Persistence
All your food entries are automatically saved to your browser's localStorage:
- **Automatic saving**: Changes persist across browser sessions
- **Daily reset**: Data clears when you reset all information
- **Privacy**: All data stays in your local browser storage

## Mobile Usage Guide

NutriTrack is fully optimized for mobile devices with responsive design and touch-friendly interfaces:

### Mobile-Specific Features
- **Touch-optimized buttons**: Larger tap targets for easy interaction
- **Responsive layout**: Adapts to various screen sizes
- **Swipe gestures**: Smooth scrolling through food lists
- **Auto-focus**: Keyboard appears automatically for form inputs

### Mobile Best Practices
- **Use landscape mode**: Better visibility for dashboard metrics
- **Enable notifications**: Allow browser notifications for reminders
- **Bookmark the page**: Add to home screen for quick access
- **Regular usage**: Log meals consistently throughout the day

### Mobile Performance Tips
- **Clear cache periodically**: Maintain optimal performance
- **Close unused tabs**: Free up browser resources
- **Use stable connection**: Ensure smooth data synchronization

## Troubleshooting Common Issues

### localStorage Access Problems
If you encounter issues with data persistence:

#### Symptom: Data doesn't save between sessions
**Solution**: 
1. Check browser privacy settings
2. Ensure localStorage is enabled
3. Disable private/incognito mode
4. Clear browser cache and cookies

#### Symptom: Error messages about storage access
**Solution**:
1. Verify browser compatibility (see requirements above)
2. Check for browser extensions blocking storage
3. Try a different browser
4. Reset browser permissions

### Display and Interface Issues

#### Symptom: Dashboard not updating
**Solution**:
1. Refresh the page (Ctrl+F5 or Cmd+Shift+R)
2. Clear browser cache
3. Check JavaScript is enabled
4. Disable browser extensions temporarily

#### Symptom: Forms not submitting
**Solution**:
1. Fill all required fields
2. Check for valid numeric input
3. Ensure proper decimal format
4. Verify internet connection for CDN resources

### Performance Issues

#### Symptom: Slow loading or lagging interface
**Solution**:
1. Close other browser tabs
2. Clear browser history and cache
3. Update to latest browser version
4. Restart the browser completely

### Data Recovery

#### Symptom: Lost food entries
**Solution**:
1. Check if using private browsing mode
2. Verify localStorage permissions
3. Try accessing from different browser
4. Contact support if data recovery needed

## Best Practices

### Daily Tracking Routine
1. **Morning setup**: Review daily goals and plan meals
2. **Immediate logging**: Record foods as soon as consumed
3. **Portion accuracy**: Use measuring tools for precise tracking
4. **Evening review**: Assess daily progress and adjust tomorrow's plan

### Goal Achievement Strategies
- **Start realistic**: Begin with achievable calorie targets
- **Gradual adjustments**: Modify goals based on progress
- **Consistent logging**: Track every meal and snack
- **Weekly reviews**: Analyze patterns and make informed adjustments

### Data Management
- **Regular backups**: Export important data if available
- **Clean entries**: Delete duplicate or incorrect items
- **Consistent naming**: Use standard food names for better tracking
- **Periodic resets**: Clear old data to maintain focus on current goals

### Privacy and Security
- **Local storage only**: All data remains on your device
- **No account required**: Complete privacy without personal information
- **Offline capability**: Works without internet connection
- **Browser security**: Leverages built-in browser security features

---

**Need Help?** If you encounter issues not covered in this guide, try refreshing the page, clearing your browser cache, or switching to a different modern browser. The application is designed to work seamlessly across all supported platforms and devices.

**Version**: NutriTrack v1.0 · Created with ❤️ for better health