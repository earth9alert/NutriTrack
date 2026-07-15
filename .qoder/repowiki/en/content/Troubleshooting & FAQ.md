# Troubleshooting & FAQ

<cite>
**Referenced Files in This Document**
- [index.html](file://index.html)
</cite>

## Table of Contents
1. [Introduction](#introduction)
2. [Common Issues and Solutions](#common-issues-and-solutions)
3. [Browser Compatibility Guide](#browser-compatibility-guide)
4. [Data Management and Backup](#data-management-and-backup)
5. [Performance Optimization](#performance-optimization)
6. [Mobile Device Considerations](#mobile-device-considerations)
7. [Debugging and Error Handling](#debugging-and-error-handling)
8. [Frequently Asked Questions](#frequently-asked-questions)
9. [Known Limitations and Workarounds](#known-limitations-and-workarounds)
10. [Reporting Issues](#reporting-issues)

## Introduction

NutriTrack is a single-file nutrition tracking application designed to help users monitor their daily caloric intake and macronutrient consumption. The application operates entirely within the browser using localStorage for data persistence, making it lightweight and easy to deploy without requiring a backend server.

This troubleshooting guide addresses common issues users may encounter, provides solutions for various compatibility problems, and offers guidance on optimizing performance and managing data effectively.

## Common Issues and Solutions

### localStorage Not Working

**Problem**: Data does not persist between sessions or disappears after closing the browser.

**Causes**:
- Browser security settings blocking localStorage access
- Private/incognito mode restrictions
- Storage quota exceeded
- Third-party cookie blockers interfering with storage

**Solutions**:
1. **Check browser storage permissions**: Ensure your browser allows local storage for the site
2. **Disable private browsing**: Use regular browsing mode instead of incognito/private windows
3. **Clear browser cache**: Sometimes corrupted cache files interfere with storage operations
4. **Check storage quota**: Large amounts of data may exceed browser limits (typically 5-10MB)

**Section sources**
- [index.html:304](file://index.html#L304)
- [index.html:370](file://index.html#L370)

### Data Persistence Problems Across Browsers

**Problem**: Data doesn't sync between different browsers or devices.

**Explanation**: NutriTrack uses browser-specific localStorage, which means data is stored separately for each browser and device.

**Solutions**:
1. **Use the same browser consistently**: Data won't transfer between Chrome, Firefox, Safari, etc.
2. **Manual backup/restore**: Use the export functionality (see below) to transfer data between browsers
3. **Cloud sync workaround**: Export data regularly and import it on other devices

**Section sources**
- [index.html:304](file://index.html#L304)

### Mobile Device Compatibility Issues

**Problem**: Application doesn't work properly on mobile devices or touch interactions are problematic.

**Solutions**:
1. **Add to home screen**: Use "Add to Home Screen" feature for app-like experience
2. **Check viewport settings**: Ensure proper mobile viewport configuration
3. **Touch target sizing**: Verify buttons and inputs are large enough for touch interaction
4. **Keyboard handling**: Be aware of virtual keyboard covering input fields

**Section sources**
- [index.html:5](file://index.html#L5)

### Performance Issues with Large Datasets

**Problem**: Application becomes slow when many food entries are accumulated over time.

**Causes**:
- DOM manipulation with large datasets
- Repeated calculations during rendering
- Memory usage from excessive data

**Solutions**:
1. **Regular data cleanup**: Delete old entries periodically
2. **Pagination implementation**: Consider implementing date-based filtering
3. **Virtual scrolling**: For very large datasets, implement virtual scrolling techniques
4. **Debounced updates**: Reduce frequency of DOM updates during bulk operations

## Browser Compatibility Guide

### Supported Browsers

| Browser | Version | Status | Notes |
|---------|---------|--------|-------|
| Chrome | 90+ | ✅ Fully Supported | Best performance and features |
| Firefox | 88+ | ✅ Fully Supported | Full localStorage support |
| Safari | 14+ | ✅ Fully Supported | iOS Safari supported |
| Edge | 90+ | ✅ Fully Supported | Chromium-based, excellent compatibility |
| Opera | 76+ | ✅ Fully Supported | Good compatibility |

### Known Browser-Specific Behaviors

**Chrome**:
- Aggressive storage clearing in some privacy modes
- May clear localStorage after extended periods of inactivity

**Firefox**:
- Enhanced Tracking Protection may block some features
- Storage limits may be more restrictive in private browsing

**Safari/iOS**:
- Strict storage quotas (5MB per domain)
- Background tab limitations
- Auto-lock may clear session data

**Section sources**
- [index.html:304](file://index.html#L304)
- [index.html:370](file://index.html#L370)

## Data Management and Backup

### Manual Data Backup

Since NutriTrack uses localStorage, there's no automatic cloud backup. Follow these steps to manually backup your data:

1. **Open Developer Tools**: Press F12 or right-click → Inspect
2. **Navigate to Application tab**: Find Local Storage section
3. **Export data**: Copy the JSON data from `nutritrack_log` key
4. **Save to file**: Paste into a text editor and save as `.json` file

### Data Import Process

To restore data on another device or browser:

1. **Open Developer Tools** on the target browser
2. **Navigate to Application tab** → Local Storage
3. **Find nutritrack_log key**
4. **Paste your backup JSON data**
5. **Refresh the page** to load the restored data

### Data Export Functionality

The current version doesn't include built-in export/import functionality. Consider adding this feature by implementing:

```javascript
// Example export function structure
function exportData() {
    const data = localStorage.getItem('nutritrack_log');
    const blob = new Blob([data], {type: 'application/json'});
    const url = URL.createObjectURL(blob);
    // Create download link
}
```

**Section sources**
- [index.html:304](file://index.html#L304)
- [index.html:370](file://index.html#L370)

## Performance Optimization

### Current Performance Characteristics

The application uses several optimization techniques:

1. **Efficient DOM updates**: Only updates necessary elements
2. **CSS transitions**: Hardware-accelerated animations
3. **Minimal reflows**: Batch DOM operations where possible
4. **Event delegation**: Efficient event handling

### Optimization Recommendations

For better performance with large datasets:

1. **Implement pagination**: Show only recent entries by default
2. **Use requestAnimationFrame**: For smooth animations
3. **Debounce user input**: Reduce calculation frequency
4. **Lazy loading**: Load additional data on demand
5. **Memory management**: Clear references to removed items

### Storage Quota Management

Monitor storage usage:

```javascript
// Check storage quota
if (navigator.storage && navigator.storage.estimate) {
    navigator.storage.estimate().then(estimate => {
        console.log('Quota:', estimate.quota);
        console.log('Usage:', estimate.usage);
    });
}
```

## Mobile Device Considerations

### Touch Interface Optimization

The application includes several mobile-friendly features:

1. **Responsive design**: Adapts to different screen sizes
2. **Touch-friendly buttons**: Adequate tap target sizes
3. **Viewport meta tag**: Proper mobile scaling
4. **Smooth scrolling**: Native scroll behavior

### Mobile-Specific Issues

**iOS Safari**:
- May require user gesture to play media
- Stricter storage policies
- Background tab limitations

**Android Chrome**:
- Better performance than iOS Safari
- More generous storage quotas
- Better developer tools support

**Section sources**
- [index.html:5](file://index.html#L5)

## Debugging and Error Handling

### Using Browser Developer Tools

**Console Tab**:
- View JavaScript errors and warnings
- Monitor localStorage operations
- Test functions interactively

**Application Tab**:
- Inspect localStorage contents
- Clear specific storage keys
- Monitor storage quota usage

**Network Tab**:
- Check CDN resource loading
- Monitor external dependencies

### Common Error Patterns

**Storage Access Errors**:
```javascript
try {
    localStorage.setItem('key', 'value');
} catch (e) {
    console.error('Storage error:', e);
    // Handle gracefully
}
```

**JSON Parsing Errors**:
```javascript
try {
    const data = JSON.parse(localStorage.getItem('key'));
} catch (e) {
    console.error('Invalid JSON data:', e);
    // Reset to default state
}
```

### Error Handling Strategies

1. **Graceful degradation**: Continue functionality even if storage fails
2. **User feedback**: Show meaningful error messages
3. **Automatic recovery**: Reset to safe defaults on corruption
4. **Logging**: Track errors for debugging

**Section sources**
- [index.html:304](file://index.html#L304)
- [index.html:370](file://index.html#L370)

## Frequently Asked Questions

### Q: How do I reset all my data?

**A**: Click the "Reset Data" button in the header. This will permanently delete all your food entries and cannot be undone.

**Section sources**
- [index.html:58](file://index.html#L58)
- [index.html:373-380](file://index.html#L373-L380)

### Q: Can I share my data between multiple devices?

**A**: Currently, data is stored locally in each browser. To share data, you'll need to manually export and import using the methods described in the Data Management section.

### Q: What happens if I clear my browser cache?

**A**: Clearing browser cache typically doesn't affect localStorage. However, clearing site data or cookies may remove your NutriTrack data. Always backup important data before clearing browser data.

### Q: How accurate are the nutritional values?

**A**: The preset foods use approximate nutritional values based on standard databases. For precise tracking, consider using official nutrition labels or verified databases. Custom entries allow you to input exact values from product packaging.

### Q: Can I customize the goal values?

**A**: The current version has hardcoded goals. You can modify the GOALS object in the source code to set custom targets:

```javascript
const GOALS = { calories: 1800, protein: 120, carbs: 150, fats: 50 };
```

**Section sources**
- [index.html:290](file://index.html#L290)

### Q: Why isn't my data showing up immediately?

**A**: The application should update instantly. If you're experiencing delays, check:
- Browser performance settings
- Ad blockers interfering with scripts
- Multiple tabs running the same application
- Low device memory

### Q: How much data can I store?

**A**: Most browsers allow 5-10MB of localStorage data. For typical usage, this should accommodate thousands of food entries. Monitor storage usage in browser developer tools.

## Known Limitations and Workarounds

### Single-File Architecture Limitations

**Current Limitations**:
1. **No automatic backups**: Manual backup required
2. **Limited customization**: Hardcoded goals and presets
3. **No user accounts**: Data tied to browser storage
4. **No real-time sync**: No multi-device synchronization
5. **Limited analytics**: Basic calorie and macro tracking only

**Workarounds**:
1. **Regular manual backups**: Use developer tools to export data
2. **Code modification**: Edit source files for customization
3. **Bookmark the page**: Save frequently accessed URLs
4. **Screen recording**: Record progress for personal records

### Feature Enhancement Suggestions

Consider implementing these improvements:

1. **Import/Export functionality**: Built-in data backup and restore
2. **Customizable goals**: User-configurable nutritional targets
3. **Food database integration**: API connections for nutritional data
4. **Progress charts**: Historical trend visualization
5. **Multi-day tracking**: Calendar view and weekly summaries

## Reporting Issues

### Before Reporting an Issue

1. **Reproduce the problem**: Try to consistently recreate the issue
2. **Check browser compatibility**: Note your browser and version
3. **Test in different environments**: Try other browsers if possible
4. **Gather diagnostic information**: Collect relevant console logs

### Information to Include

When reporting bugs, provide:

1. **Browser details**: Name, version, operating system
2. **Steps to reproduce**: Detailed sequence of actions
3. **Expected vs actual behavior**: What should happen vs what did happen
4. **Error messages**: Any console errors or alerts
5. **Screenshots**: Visual evidence of the problem
6. **Data sample**: Sample of your data (if relevant)

### Debug Checklist

- [ ] Console shows no JavaScript errors
- [ ] localStorage is accessible and writable
- [ ] Network requests complete successfully
- [ ] Page renders correctly on different screen sizes
- [ ] Touch interactions work on mobile devices
- [ ] Data persists after page refresh

### Getting Help

If you need assistance:

1. **Check this troubleshooting guide** first
2. **Search online forums** for similar issues
3. **Contact support** with detailed bug reports
4. **Contribute fixes** if you have development skills

---

*Last updated: Based on NutriTrack v1.0 architecture analysis*