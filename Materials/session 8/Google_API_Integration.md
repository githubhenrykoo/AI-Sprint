# Google API Integration Guide

## Table of Contents
1. [What are Google APIs?](#what-are-google-apis)
2. [Popular Google APIs](#popular-google-apis)
3. [Getting Started](#getting-started)
4. [Setting Up Your First Google API](#setting-up-your-first-google-api)
5. [Authentication](#authentication)
6. [Making Your First API Call](#making-your-first-api-call)
7. [Common Use Cases](#common-use-cases)
8. [Best Practices](#best-practices)
9. [Troubleshooting](#troubleshooting)

## What are Google APIs?

Google APIs are services provided by Google that let your applications access Google's powerful tools and data. Think of them as ready-made features you can add to your apps without building everything from scratch.

### Why Use Google APIs?

- **Save Development Time**: Use Google's proven technology instead of building your own
- **Access Powerful Features**: Maps, translation, AI, cloud storage, and more
- **Reliable and Scalable**: Google's infrastructure handles millions of requests
- **Regular Updates**: Google continuously improves their services

## Popular Google APIs

### 1. **Google Maps API**
- **What it does**: Add maps, directions, and location services to your app
- **Use cases**: Store locators, delivery tracking, travel apps
- **Example**: Show nearby restaurants on a map

### 2. **Google Translate API**
- **What it does**: Translate text between 100+ languages
- **Use cases**: Multi-language websites, chat apps, travel apps
- **Example**: Translate user reviews in real-time

### 3. **Google Drive API**
- **What it does**: Access and manage files in Google Drive
- **Use cases**: Backup apps, document collaboration, file sharing
- **Example**: Save app data to user's Google Drive

### 4. **YouTube API**
- **What it does**: Access YouTube videos, channels, and playlists
- **Use cases**: Video apps, content management, analytics
- **Example**: Display your company's YouTube videos in your app

### 5. **Gmail API**
- **What it does**: Read, send, and manage Gmail messages
- **Use cases**: Email clients, automation tools, notifications
- **Example**: Send automated email receipts

### 6. **Google Calendar API**
- **What it does**: Create and manage calendar events
- **Use cases**: Scheduling apps, booking systems, reminders
- **Example**: Book appointments directly into user's calendar

## Getting Started

### Step 1: Create a Google Cloud Project

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Click "Create Project"
3. Give your project a name (like "My First API Project")
4. Click "Create"

### Step 2: Enable the API You Want to Use

1. In your project, go to "APIs & Services" → "Library"
2. Search for the API you want (e.g., "Maps API")
3. Click on it and press "Enable"

### Step 3: Create Credentials

1. Go to "APIs & Services" → "Credentials"
2. Click "Create Credentials" → "API Key"
3. Copy your API key and keep it safe!

## Setting Up Your First Google API

Let's use Google Maps API as an example:

### 1. Enable Google Maps JavaScript API
- In Google Cloud Console, search for "Maps JavaScript API"
- Click "Enable"

### 2. Get Your API Key
- Go to Credentials
- Create a new API key
- **Important**: Restrict your key to prevent unauthorized use

### 3. Basic HTML Example

```html
<!DOCTYPE html>
<html>
<head>
    <title>My First Google Map</title>
</head>
<body>
    <div id="map" style="height: 400px; width: 100%;"></div>
    
    <script>
        function initMap() {
            // Create a map centered on Bangkok
            const map = new google.maps.Map(document.getElementById("map"), {
                zoom: 13,
                center: { lat: 13.7563, lng: 100.5018 }
            });
            
            // Add a marker
            new google.maps.Marker({
                position: { lat: 13.7563, lng: 100.5018 },
                map: map,
                title: "Bangkok, Thailand"
            });
        }
    </script>
    
    <!-- Load Google Maps API -->
    <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap"></script>
</body>
</html>
```

## Authentication

### API Keys (Simplest)
- Good for public data and simple applications
- Include in your requests like: `?key=YOUR_API_KEY`
- **Security**: Restrict by website, IP, or API

### OAuth 2.0 (For User Data)
- Required when accessing user's private data (Gmail, Drive, etc.)
- User logs in with their Google account
- Your app gets permission to access their data

### Service Accounts (For Server Applications)
- For server-to-server communication
- No user interaction required
- Good for automated tasks

## Making Your First API Call

### Example: Google Translate API

```javascript
// Simple translation request
const translateText = async (text, targetLanguage) => {
    const apiKey = 'YOUR_API_KEY';
    const url = `https://translation.googleapis.com/language/translate/v2?key=${apiKey}`;
    
    const response = await fetch(url, {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({
            q: text,
            target: targetLanguage,
            source: 'en'
        })
    });
    
    const data = await response.json();
    return data.data.translations[0].translatedText;
};

// Use it
translateText("Hello, world!", "th").then(result => {
    console.log(result); // สวัสดีชาวโลก!
});
```

### Example: YouTube API (Get Channel Info)

```javascript
const getChannelInfo = async (channelId) => {
    const apiKey = 'YOUR_API_KEY';
    const url = `https://www.googleapis.com/youtube/v3/channels?part=snippet,statistics&id=${channelId}&key=${apiKey}`;
    
    const response = await fetch(url);
    const data = await response.json();
    
    return {
        name: data.items[0].snippet.title,
        subscribers: data.items[0].statistics.subscriberCount,
        description: data.items[0].snippet.description
    };
};
```

## Common Use Cases

### 1. **Restaurant Finder App**
- **Google Maps API**: Show restaurant locations
- **Google Places API**: Get restaurant details and reviews
- **Google Directions API**: Show route to restaurant

### 2. **Travel Planning App**
- **Google Translate API**: Translate phrases for travelers
- **Google Maps API**: Show destinations and routes
- **Google Calendar API**: Add travel dates to calendar

### 3. **Business Website**
- **Google Maps API**: Show office location
- **Gmail API**: Contact form submissions
- **Google Analytics API**: Track website performance

### 4. **Educational App**
- **YouTube API**: Embed educational videos
- **Google Drive API**: Store and share course materials
- **Google Translate API**: Support multiple languages

## Best Practices

### 1. **Secure Your API Keys**
- Never put API keys in client-side code that users can see
- Use environment variables for server applications
- Restrict API keys to specific websites or IP addresses
- Regularly rotate your API keys

### 2. **Handle Errors Gracefully**
```javascript
try {
    const result = await makeAPICall();
    // Handle success
} catch (error) {
    if (error.status === 429) {
        // Too many requests - wait and retry
        console.log("Rate limit exceeded, please wait");
    } else if (error.status === 401) {
        // Invalid API key
        console.log("Check your API key");
    } else {
        // Other errors
        console.log("Something went wrong:", error.message);
    }
}
```

### 3. **Respect Rate Limits**
- Don't make too many requests too quickly
- Implement retry logic with exponential backoff
- Cache responses when possible

### 4. **Monitor Your Usage**
- Check Google Cloud Console regularly
- Set up billing alerts
- Monitor for unusual activity

## Troubleshooting

### Common Issues and Solutions

#### "API key not valid"
- Check if the API is enabled in Google Cloud Console
- Verify the API key is correct
- Make sure the key isn't restricted to other websites

#### "Quota exceeded"
- You've hit your daily/monthly limit
- Upgrade your plan or wait for reset
- Optimize your code to make fewer requests

#### "Access denied"
- Check if you need OAuth instead of API key
- Verify the user has given proper permissions
- Make sure your OAuth setup is correct

#### Map not loading
- Check if Maps JavaScript API is enabled
- Verify your API key in the script tag
- Check browser console for error messages

### Getting Help

1. **Google API Documentation**: Each API has detailed docs with examples
2. **Stack Overflow**: Search for your specific error message
3. **Google Cloud Support**: For billing and account issues
4. **Community Forums**: Google Developers community

## Practice Exercises

### Beginner
1. Create a simple webpage with a Google Map showing your location
2. Use Google Translate API to translate "Hello" into 5 different languages
3. Display a YouTube video on your webpage using YouTube API

### Intermediate
1. Build a restaurant finder that shows nearby restaurants on a map
2. Create a multi-language website using Google Translate API
3. Build a simple calendar app using Google Calendar API

### Advanced
1. Create a travel planning app combining Maps, Translate, and Calendar APIs
2. Build a content management system using Google Drive API
3. Develop a business dashboard using multiple Google APIs

## Summary

Google APIs provide powerful, ready-to-use functionality that can make your applications much more capable. Key points to remember:

- **Start Simple**: Begin with one API and basic functionality
- **Security First**: Always protect your API keys and user data
- **Read the Docs**: Each API has specific requirements and best practices
- **Monitor Usage**: Keep track of your API calls and costs
- **Handle Errors**: Always plan for when things go wrong

With Google APIs, you can add professional-grade features to your applications without building everything from scratch. Start with a simple project and gradually explore more advanced features as you become comfortable with the basics.
