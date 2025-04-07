import React, { useState, useEffect } from 'react';

const WorldClock = () => {
  // State to hold the current time
  const [currentTime, setCurrentTime] = useState(new Date());
  // State to hold the selected time zone
  const [selectedTimeZone, setSelectedTimeZone] = useState('America/New_York');
  // State to hold the selected theme
  const [selectedTheme, setSelectedTheme] = useState('blue-purple');
  
  // Theme options
  const themes = [
    { name: 'Blue Purple', value: 'blue-purple', classes: 'from-blue-500 via-purple-500 to-pink-500' },
    { name: 'Green Blue', value: 'green-blue', classes: 'from-green-400 via-teal-500 to-blue-500' },
    { name: 'Orange Red', value: 'orange-red', classes: 'from-yellow-400 via-orange-500 to-red-500' },
    { name: 'Purple Pink', value: 'purple-pink', classes: 'from-indigo-500 via-purple-500 to-pink-500' },
    { name: 'Teal Purple', value: 'teal-purple', classes: 'from-teal-400 via-blue-500 to-purple-600' },
  ];
  
  // US and international time zones
  const timeZones = [
    { name: 'Eastern Time (ET)', zone: 'America/New_York' },
    { name: 'Central Time (CT)', zone: 'America/Chicago' },
    { name: 'Mountain Time (MT)', zone: 'America/Denver' },
    { name: 'Pacific Time (PT)', zone: 'America/Los_Angeles' },
    { name: 'Alaska Time (AKT)', zone: 'America/Anchorage' },
    { name: 'Hawaii Time (HST)', zone: 'Pacific/Honolulu' },
    { name: 'London (GMT)', zone: 'Europe/London' },
    { name: 'Paris (CET)', zone: 'Europe/Paris' },
    { name: 'Tokyo (JST)', zone: 'Asia/Tokyo' },
    { name: 'Sydney (AEST)', zone: 'Australia/Sydney' }
  ];

  // Update the time every second
  useEffect(() => {
    const timer = setInterval(() => {
      setCurrentTime(new Date());
    }, 1000);
    
    return () => {
      clearInterval(timer);
    };
  }, []);

  // Format time for a specific timezone
  const formatTimeForZone = (date, timeZone) => {
    return new Intl.DateTimeFormat('en-US', {
      timeZone,
      hour: '2-digit',
      minute: '2-digit',
      second: '2-digit',
      hour12: true,
    }).format(date);
  };

  // Format date for a specific timezone
  const formatDateForZone = (date, timeZone) => {
    return new Intl.DateTimeFormat('en-US', {
      timeZone,
      weekday: 'long',
      year: 'numeric',
      month: 'long',
      day: 'numeric',
    }).format(date);
  };

  // Handle time zone change
  const handleTimeZoneChange = (e) => {
    setSelectedTimeZone(e.target.value);
  };
  
  // Handle theme change
  const handleThemeChange = (e) => {
    setSelectedTheme(e.target.value);
  };
  
  // Get current theme classes
  const getCurrentThemeClasses = () => {
    return themes.find(theme => theme.value === selectedTheme)?.classes || themes[0].classes;
  };

  return (
    <div className={`min-h-screen flex items-center justify-center bg-gradient-to-br ${getCurrentThemeClasses()}`}>
      <div className="w-full max-w-md bg-white bg-opacity-20 backdrop-blur-lg rounded-xl shadow-lg p-8">
        <h1 className="text-3xl font-bold text-white text-center mb-6">World Clock</h1>
        
        <div className="mb-4">
          <label htmlFor="timeZoneSelect" className="block text-white mb-2">Select Time Zone:</label>
          <select 
            id="timeZoneSelect"
            value={selectedTimeZone}
            onChange={handleTimeZoneChange}
            className="w-full p-2 rounded-lg bg-white bg-opacity-30 text-white border border-white border-opacity-30 focus:outline-none focus:ring-2 focus:ring-white"
          >
            {timeZones.map((tz) => (
              <option key={tz.zone} value={tz.zone} className="text-black">
                {tz.name}
              </option>
            ))}
          </select>
        </div>
        
        <div className="mb-6">
          <label htmlFor="themeSelect" className="block text-white mb-2">Select Theme:</label>
          <select 
            id="themeSelect"
            value={selectedTheme}
            onChange={handleThemeChange}
            className="w-full p-2 rounded-lg bg-white bg-opacity-30 text-white border border-white border-opacity-30 focus:outline-none focus:ring-2 focus:ring-white"
          >
            {themes.map((theme) => (
              <option key={theme.value} value={theme.value} className="text-black">
                {theme.name}
              </option>
            ))}
          </select>
        </div>
        
        <div className="bg-white bg-opacity-30 rounded-lg p-6 shadow-md hover:shadow-lg transition-shadow text-center">
          <h2 className="text-xl font-semibold text-white mb-2">
            {timeZones.find(tz => tz.zone === selectedTimeZone)?.name}
          </h2>
          <div className="text-5xl font-bold text-white mb-2">
            {formatTimeForZone(currentTime, selectedTimeZone)}
          </div>
          <div className="text-lg text-white">
            {formatDateForZone(currentTime, selectedTimeZone)}
          </div>
        </div>
        
        <div className="mt-6 text-white text-sm opacity-80 text-center">
          © {new Date().getFullYear()} World Clock App
        </div>
      </div>
    </div>
  );
};

export default WorldClock;
