# YOPHORIA_INNOVALITON_CHALLENGE
Gen Z Edu tech for Yophoria innovation challenge hackathon
import React, { useState, useEffect } from 'react';
import { 
  MessageCircle, 
  Brain, 
  Trophy, 
  Users, 
  Zap, 
  Sparkles, 
  Heart, 
  TrendingUp, 
  Calendar, 
  Clock,
  Share2,
  Star,
  Play,
  Mic,
  Camera,
  BookOpen,
  Award,
  MessageSquare,
  User,
  Settings,
  ChevronRight,
  Plus,
  Send
} from 'lucide-react';

const App = () => {
  const [activeTab, setActiveTab] = useState('dashboard');
  const [companion, setCompanion] = useState({
    name: "Nova",
    mood: "excited",
    level: 12,
    streak: 7,
    avatar: "https://placehold.co/80x80/6366f1/white?text=N"
  });
  const [user, setUser] = useState({
    name: "Alex",
    points: 2450,
    level: 8,
    friends: 12
  });
  const [messages, setMessages] = useState([
    { id: 1, text: "Hey Alex! Ready to tackle calculus today? I've got some fun interactive problems for you!", sender: "companion", timestamp: "2 min ago" },
    { id: 2, text: "I'm struggling with derivatives...", sender: "user", timestamp: "1 min ago" },
    { id: 3, text: "No worries! Let's break it down together. Want to try a visual approach?", sender: "companion", timestamp: "just now" }
  ]);
  const [newMessage, setNewMessage] = useState('');
  const [activeSubject, setActiveSubject] = useState('Math');

  // Mock data for subjects
  const subjects = [
    { name: 'Math', progress: 75, icon: <BookOpen className="w-5 h-5" /> },
    { name: 'Science', progress: 60, icon: <Brain className="w-5 h-5" /> },
    { name: 'History', progress: 40, icon: <BookOpen className="w-5 h-5" /> },
    { name: 'Languages', progress: 90, icon: <MessageSquare className="w-5 h-5" /> }
  ];

  // Mock data for achievements
  const achievements = [
    { id: 1, title: "First Steps", description: "Complete your first lesson", unlocked: true, icon: <Award className="w-4 h-4" /> },
    { id: 2, title: "Streak Master", description: "7-day learning streak", unlocked: true, icon: <Trophy className="w-4 h-4" /> },
    { id: 3, title: "Math Whiz", description: "Score 90% on calculus test", unlocked: false, icon: <Brain className="w-4 h-4" /> }
  ];

  // Mock data for friends
  const friends = [
    { id: 1, name: "Jamie", avatar: "https://placehold.co/40x40/f59e0b/white?text=J", status: "online", streak: 5 },
    { id: 2, name: "Taylor", avatar: "https://placehold.co/40x40/10b981/white?text=T", status: "online", streak: 12 },
    { id: 3, name: "Morgan", avatar: "https://placehold.co/40x40/ef4444/white?text=M", status: "offline", streak: 3 }
  ];

  const handleSendMessage = () => {
    if (newMessage.trim() === '') return;
    
    const userMessage = {
      id: messages.length + 1,
      text: newMessage,
      sender: 'user',
      timestamp: 'just now'
    };
    
    setMessages([...messages, userMessage]);
    setNewMessage('');
    
    // Simulate companion response after delay
    setTimeout(() => {
      const responses = [
        "That's a great question! Let me explain it in a different way.",
        "I love your curiosity! Here's how we can approach this...",
        "Interesting perspective! Have you considered this angle?",
        "You're making great progress! Let's build on that idea."
      ];
      const randomResponse = responses[Math.floor(Math.random() * responses.length)];
      
      const companionMessage = {
        id: messages.length + 2,
        text: randomResponse,
        sender: 'companion',
        timestamp: 'just now'
      };
      
      setMessages(prev => [...prev, companionMessage]);
    }, 1000);
  };

  const renderDashboard = () => (
    <div className="space-y-6">
      {/* Hero Section */}
      <div className="bg-gradient-to-r from-indigo-500 to-purple-600 rounded-2xl p-6 text-white">
        <div className="flex items-center justify-between">
          <div>
            <h1 className="text-2xl font-bold">Hey {user.name}! 👋</h1>
            <p className="mt-1 opacity-90">Ready to level up your knowledge today?</p>
          </div>
          <div className="flex items-center space-x-4">
            <div className="text-center">
              <div className="text-2xl font-bold">{user.points}</div>
              <div className="text-xs opacity-80">Points</div>
            </div>
            <div className="text-center">
              <div className="text-2xl font-bold">{user.level}</div>
              <div className="text-xs opacity-80">Level</div>
            </div>
          </div>
        </div>
        
        <div className="mt-6 flex items-center">
          <div className="bg-white/20 backdrop-blur-sm rounded-xl p-4 flex-1">
            <div className="flex items-center">
              <img 
                src={companion.avatar} 
                alt={companion.name} 
                className="w-12 h-12 rounded-full mr-3"
              />
              <div>
                <div className="font-bold">{companion.name}</div>
                <div className="text-sm flex items-center">
                  <Heart className="w-3 h-3 mr-1 text-pink-300" />
                  {companion.mood} • Level {companion.level}
                </div>
              </div>
            </div>
          </div>
          
          <button className="ml-4 bg-white text-indigo-600 px-4 py-2 rounded-full font-medium flex items-center">
            <Zap className="w-4 h-4 mr-1" />
            Quick Start
          </button>
        </div>
      </div>
      
      {/* Stats & Quick Actions */}
      <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
        <div className="bg-white rounded-xl p-4 shadow-sm border border-gray-100">
          <div className="flex items-center justify-between">
            <div>
              <p className="text-gray-500 text-sm">Current Streak</p>
              <p className="text-2xl font-bold text-indigo-600">{companion.streak} days</p>
            </div>
            <div className="bg-indigo-100 p-3 rounded-full">
              <TrendingUp className="w-6 h-6 text-indigo-600" />
            </div>
          </div>
        </div>
        
        <div className="bg-white rounded-xl p-4 shadow-sm border border-gray-100">
          <div className="flex items-center justify-between">
            <div>
              <p className="text-gray-500 text-sm">Friends Learning</p>
              <p className="text-2xl font-bold text-purple-600">{user.friends}</p>
            </div>
            <div className="bg-purple-100 p-3 rounded-full">
              <Users className="w-6 h-6 text-purple-600" />
            </div>
          </div>
        </div>
        
        <div className="bg-white rounded-xl p-4 shadow-sm border border-gray-100">
          <div className="flex items-center justify-between">
            <div>
              <p className="text-gray-500 text-sm">Today's Goal</p>
              <p className="text-2xl font-bold text-green-600">3 lessons</p>
            </div>
            <div className="bg-green-100 p-3 rounded-full">
              <Calendar className="w-6 h-6 text-green-600" />
            </div>
          </div>
        </div>
      </div>
      
      {/* Subject Progress */}
      <div className="bg-white rounded-xl p-5 shadow-sm border border-gray-100">
        <div className="flex justify-between items-center mb-4">
          <h2 className="font-bold text-lg">Your Subjects</h2>
          <button className="text-indigo-600 font-medium flex items-center">
            View All <ChevronRight className="w-4 h-4 ml-1" />
          </button>
        </div>
        
        <div className="space-y-4">
          {subjects.map((subject, index) => (
            <div key={index} className="flex items-center">
              <div className="mr-3 text-indigo-600">
                {subject.icon}
              </div>
              <div className="flex-1">
                <div className="flex justify-between mb-1">
                  <span className="font-medium">{subject.name}</span>
                  <span className="text-sm text-gray-500">{subject.progress}%</span>
                </div>
                <div className="w-full bg-gray-200 rounded-full h-2">
                  <div 
                    className="bg-gradient-to-r from-indigo-500 to-purple-600 h-2 rounded-full" 
                    style={{ width: `${subject.progress}%` }}
                  ></div>
                </div>
              </div>
            </div>
          ))}
        </div>
      </div>
      
      {/* Quick Challenge */}
      <div className="bg-gradient-to-r from-amber-400 to-orange-500 rounded-2xl p-5 text-white">
        <div className="flex items-center">
          <div className="mr-4">
            <Sparkles className="w-10 h-10" />
          </div>
          <div>
            <h3 className="font-bold text-lg">Daily Challenge!</h3>
            <p className="opacity-90">Complete 3 math problems in 5 minutes</p>
            <button className="mt-2 bg-white text-amber-600 px-4 py-1.5 rounded-full text-sm font-medium flex items-center">
              Start Now <Play className="w-3 h-3 ml-1" />
            </button>
          </div>
        </div>
      </div>
    </div>
  );

  const renderChat = () => (
    <div className="flex flex-col h-full">
      <div className="bg-gradient-to-r from-indigo-500 to-purple-600 p-4 rounded-t-2xl text-white">
        <div className="flex items-center">
          <img 
            src={companion.avatar} 
            alt={companion.name} 
            className="w-10 h-10 rounded-full mr-3"
          />
          <div>
            <div className="font-bold">{companion.name}</div>
            <div className="text-xs flex items-center">
              <div className="w-2 h-2 bg-green-400 rounded-full mr-1"></div>
              Online • {companion.mood}
            </div>
          </div>
        </div>
      </div>
      
      <div className="flex-1 p-4 overflow-y-auto space-y-4">
        {messages.map((message) => (
          <div 
            key={message.id} 
            className={`flex ${message.sender === 'user' ? 'justify-end' : 'justify-start'}`}
          >
            <div 
              className={`max-w-xs md:max-w-md px-4 py-2 rounded-2xl ${
                message.sender === 'user' 
                  ? 'bg-indigo-500 text-white rounded-br-none' 
                  : 'bg-gray-100 text-gray-800 rounded-bl-none'
              }`}
            >
              {message.text}
              <div className={`text-xs mt-1 ${message.sender === 'user' ? 'text-indigo-200' : 'text-gray-500'}`}>
                {message.timestamp}
              </div>
            </div>
          </div>
        ))}
      </div>
      
      <div className="p-4 border-t border-gray-200">
        <div className="flex items-center">
          <input
            type="text"
            value={newMessage}
            onChange={(e) => setNewMessage(e.target.value)}
            placeholder="Ask anything..."
            className="flex-1 border border-gray-300 rounded-full px-4 py-2 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:border-transparent"
            onKeyPress={(e) => e.key === 'Enter' && handleSendMessage()}
          />
          <button 
            onClick={handleSendMessage}
            className="ml-2 bg-indigo-600 text-white p-2 rounded-full hover:bg-indigo-700"
          >
            <Send className="w-5 h-5" />
          </button>
          <div className="flex ml-2 space-x-1">
            <button className="p-2 text-gray-500 hover:bg-gray-100 rounded-full">
              <Mic className="w-5 h-5" />
            </button>
            <button className="p-2 text-gray-500 hover:bg-gray-100 rounded-full">
              <Camera className="w-5 h-5" />
            </button>
          </div>
        </div>
      </div>
    </div>
  );

  const renderAchievements = () => (
    <div className="space-y-4">
      <div className="bg-gradient-to-r from-rose-500 to-pink-600 rounded-2xl p-5 text-white">
        <h2 className="font-bold text-xl">Your Achievements</h2>
        <p className="opacity-90 mt-1">Keep learning to unlock more!</p>
      </div>
      
      <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
        {achievements.map((achievement) => (
          <div 
            key={achievement.id} 
            className={`rounded-xl p-4 border ${
              achievement.unlocked 
                ? 'bg-gradient-to-br from-amber-50 to-orange-50 border-amber-200' 
                : 'bg-gray-50 border-gray-200'
            }`}
          >
            <div className="flex items-start">
              <div className={`p-2 rounded-lg mr-3 ${
                achievement.unlocked ? 'bg-amber-100 text-amber-600' : 'bg-gray-200 text-gray-500'
              }`}>
                {achievement.icon}
              </div>
              <div>
                <h3 className={`font-bold ${achievement.unlocked ? 'text-amber-800' : 'text-gray-500'}`}>
                  {achievement.title}
                </h3>
                <p className="text-sm text-gray-600 mt-1">{achievement.description}</p>
                {achievement.unlocked && (
                  <div className="mt-2 flex items-center text-amber-600">
                    <Star className="w-4 h-4 mr-1" />
                    <span className="text-xs">Unlocked!</span>
                  </div>
                )}
              </div>
            </div>
          </div>
        ))}
      </div>
    </div>
  );

  const renderSocial = () => (
    <div className="space-y-6">
      <div className="bg-gradient-to-r from-emerald-500 to-teal-600 rounded-2xl p-5 text-white">
        <h2 className="font-bold text-xl">Learning Together</h2>
        <p className="opacity-90 mt-1">Study with friends and share your progress!</p>
      </div>
      
      <div className="bg-white rounded-xl p-5 shadow-sm border border-gray-100">
        <div className="flex justify-between items-center mb-4">
          <h3 className="font-bold">Your Friends</h3>
          <button className="text-indigo-600 font-medium flex items-center">
            Invite Friends <Plus className="w-4 h-4 ml-1" />
          </button>
        </div>
        
        <div className="space-y-4">
          {friends.map((friend) => (
            <div key={friend.id} className="flex items-center">
              <div className="relative">
                <img 
                  src={friend.avatar} 
                  alt={friend.name} 
                  className="w-12 h-12 rounded-full"
                />
                <div className={`absolute bottom-0 right-0 w-3 h-3 rounded-full border-2 border-white ${
                  friend.status === 'online' ? 'bg-green-500' : 'bg-gray-400'
                }`}></div>
              </div>
              <div className="ml-3 flex-1">
                <div className="font-medium">{friend.name}</div>
                <div className="flex items-center text-sm text-gray-500">
                  <TrendingUp className="w-3 h-3 mr-1" />
                  {friend.streak}-day streak
                </div>
              </div>
              <button className="text-indigo-600">
                <Share2 className="w-5 h-5" />
              </button>
            </div>
          ))}
        </div>
      </div>
      
      <div className="bg-white rounded-xl p-5 shadow-sm border border-gray-100">
        <h3 className="font-bold mb-3">Viral Challenges</h3>
        <div className="bg-gradient-to-r from-purple-50 to-indigo-50 rounded-xl p-4 border border-purple-200">
          <div className="flex items-center">
            <div className="mr-3">
              <Trophy className="w-8 h-8 text-purple-600" />
            </div>
            <div>
              <h4 className="font-bold text-purple-800">Math Masters Challenge</h4>
              <p className="text-sm text-purple-700">Complete 5 calculus problems with friends</p>
              <div className="mt-2 flex">
                <div className="w-6 h-6 rounded-full bg-indigo-500 flex items-center justify-center text-white text-xs">3</div>
                <div className="w-6 h-6 rounded-full bg-purple-500 -ml-2 flex items-center justify-center text-white text-xs">2</div>
                <div className="w-6 h-6 rounded-full bg-pink-500 -ml-2 flex items-center justify-center text-white text-xs">1</div>
                <div className="ml-2 text-sm text-gray-500">+2 more</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  );

  return (
    <div className="min-h-screen bg-gray-50">
      {/* Header */}
      <header className="bg-white shadow-sm">
        <div className="max-w-4xl mx-auto px-4 py-3 flex justify-between items-center">
          <div className="flex items-center">
            <div className="bg-gradient-to-r from-indigo-600 to-purple-600 w-10 h-10 rounded-lg flex items-center justify-center">
              <Brain className="w-6 h-6 text-white" />
            </div>
            <h1 className="ml-3 text-xl font-bold bg-gradient-to-r from-indigo-600 to-purple-600 bg-clip-text text-transparent">
              StudyBuddy AI
            </h1>
          </div>
          
          <div className="flex items-center space-x-4">
            <button className="p-2 text-gray-500 hover:bg-gray-100 rounded-full">
              <Settings className="w-5 h-5" />
            </button>
            <div className="flex items-center">
              <div className="w-8 h-8 rounded-full bg-gradient-to-r from-amber-400 to-orange-500 flex items-center justify-center text-white font-bold">
                {user.name.charAt(0)}
              </div>
            </div>
          </div>
        </div>
      </header>
      
      <div className="max-w-4xl mx-auto px-4 py-6">
        {/* Navigation Tabs */}
        <div className="flex border-b border-gray-200 mb-6">
          {[
            { id: 'dashboard', label: 'Dashboard', icon: <Brain className="w-5 h-5" /> },
            { id: 'chat', label: 'Chat', icon: <MessageCircle className="w-5 h-5" /> },
            { id: 'achievements', label: 'Achievements', icon: <Trophy className="w-5 h-5" /> },
            { id: 'social', label: 'Social', icon: <Users className="w-5 h-5" /> }
          ].map((tab) => (
            <button
              key={tab.id}
              onClick={() => setActiveTab(tab.id)}
              className={`flex items-center px-4 py-3 font-medium text-sm ${
                activeTab === tab.id
                  ? 'text-indigo-600 border-b-2 border-indigo-600'
                  : 'text-gray-500 hover:text-gray-700'
              }`}
            >
              {tab.icon}
              <span className="ml-2">{tab.label}</span>
            </button>
          ))}
        </div>
        
        {/* Main Content */}
        <div className="bg-white rounded-2xl shadow-sm overflow-hidden">
          {activeTab === 'dashboard' && renderDashboard()}
          {activeTab === 'chat' && renderChat()}
          {activeTab === 'achievements' && renderAchievements()}
          {activeTab === 'social' && renderSocial()}
        </div>
        
        {/* Subject Selector */}
        <div className="mt-6 flex flex-wrap gap-2">
          {subjects.map((subject) => (
            <button
              key={subject.name}
              onClick={() => setActiveSubject(subject.name)}
              className={`px-4 py-2 rounded-full text-sm font-medium flex items-center ${
                activeSubject === subject.name
                  ? 'bg-indigo-600 text-white'
                  : 'bg-white text-gray-700 border border-gray-200'
              }`}
            >
              {subject.icon}
              <span className="ml-2">{subject.name}</span>
            </button>
          ))}
        </div>
      </div>
      
      {/* Floating Action Button */}
      <button className="fixed bottom-6 right-6 bg-gradient-to-r from-indigo-600 to-purple-600 text-white p-4 rounded-full shadow-lg hover:shadow-xl transition-shadow">
        <Zap className="w-6 h-6" />
      </button>
    </div>
  );
};

export default App;
