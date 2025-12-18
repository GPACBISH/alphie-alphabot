"use client";
import React, { useState, useEffect, useRef } from 'react';

/** * ALPHIE ALPHA CLUB - VERCEL DEPLOYABLE VERSION
 * This file combines the Retro Dashboard, Arcade, and the Cinema Club Page.
 */

// --- STYLES & ANIMATIONS ---
const GlobalStyles = () => (
  <style jsx global>{`
    @import url('https://fonts.googleapis.com/css2?family=Pacifico&family=Space+Mono:wght@400;700&family=Playfair+Display:ital,wght@1,900&display=swap');
    
    :root {
      --cream: #FDFBF7;
      --forest: #1A4D2E;
      --gold: #D4AF37;
      --red: #8B0000;
    }

    body { background-color: var(--cream); color: var(--forest); font-family: 'Space Mono', monospace; overflow-x: hidden; }
    
    .shadow-retro { box-shadow: 5px 5px 0px 0px var(--forest); }
    .shadow-retro-hover { box-shadow: 2px 2px 0px 0px var(--forest); }
    .gold-shimmer-text {
      background: linear-gradient(to right, #bf953f, #fcf6ba, #b38728, #fbf5b7, #aa771c);
      background-size: 200% auto;
      color: transparent;
      -webkit-background-clip: text;
      background-clip: text;
      animation: shine 3s linear infinite;
    }
    @keyframes shine { to { background-position: 200% center; } }
    
    .velvet-curtain {
      background: repeating-linear-gradient(90deg, #600000, #600000 20px, #8B0000 40px, #600000 60px);
      box-shadow: inset 0 0 50px rgba(0,0,0,0.8);
    }

    .spotlight-mask {
      background: radial-gradient(circle at center, transparent 150px, rgba(0,0,0,0.95) 400px);
    }
  `}</style>
);

// --- COMPONENTS ---

const CuteAlphie = () => (
  <div className="w-48 h-48 mx-auto relative mb-4 animate-bounce">
    <svg viewBox="0 0 200 200" className="w-full h-full drop-shadow-xl">
      <path d="M50 180 C 40 180, 20 120, 50 80 C 70 50, 130 50, 150 80 C 180 120, 160 180, 150 180 Z" fill="#A0AEC0" stroke="#1A4D2E" strokeWidth="3"/>
      <ellipse cx="100" cy="130" rx="35" ry="30" fill="#E2E8F0" opacity="0.6"/>
      <rect x="70" y="25" width="60" height="45" fill="#1A4D2E" stroke="black" strokeWidth="2"/>
      <rect x="70" y="55" width="60" height="10" fill="#D4AF37" />
      <circle cx="125" cy="80" r="12" stroke="#D4AF37" strokeWidth="2" fill="rgba(212, 175, 55, 0.2)" />
      <circle cx="75" cy="80" r="5" fill="black" />
      <circle cx="125" cy="80" r="5" fill="black" />
    </svg>
  </div>
);

const JoinClubPage = () => {
  const [stage, setStage] = useState(0);
  useEffect(() => {
    const sequence = [
      () => setStage(1), // Open Curtains
      () => setStage(2), // Spotlight
      () => setStage(3), // Flash
      () => setStage(4)  // Buttons
    ];
    sequence.forEach((fn, i) => setTimeout(fn, [100, 2500, 3000, 4500][i]));
  }, []);

  return (
    <div className="fixed inset-0 z-50 overflow-hidden flex flex-col items-center">
      <div className={`absolute top-0 left-0 w-1/2 h-full z-50 velvet-curtain transition-transform duration-[2000ms] ${stage >= 1 ? '-translate-x-full' : 'translate-x-0'}`} />
      <div className={`absolute top-0 right-0 w-1/2 h-full z-50 velvet-curtain transition-transform duration-[2000ms] ${stage >= 1 ? 'translate-x-full' : 'translate-x-0'}`} />
      
      <div className={`relative w-full h-full flex flex-col items-center justify-center transition-colors duration-[2000ms] ${stage < 4 ? 'bg-black' : 'bg-[#1a1a1a]'}`}>
        <div className={`absolute inset-0 pointer-events-none transition-opacity duration-1000 ${stage === 2 || stage === 3 ? 'opacity-100' : 'opacity-0'} spotlight-mask`} />
        
        <h1 className="font-serif italic font-black text-6xl md:text-8xl gold-shimmer-text tracking-widest rotate-[-5deg]">
          Alpha Club
        </h1>

        <div className={`mt-20 flex flex-col gap-6 transition-all duration-1000 ${stage === 4 ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'}`}>
          <button className="bg-[#D4AF37] text-[#1A4D2E] font-black py-4 px-12 rounded-full border-4 border-[#1A4D2E] shadow-xl hover:scale-105 transition-transform">
            JOIN THE CLUB
          </button>
        </div>
      </div>
    </div>
  );
};

// --- MAIN APP ---

export default function App() {
  const [page, setPage] = useState('home');
  const [chatInput, setChatInput] = useState("");
  const [chatHistory, setChatHistory] = useState([{ text: "Welcome to the Club. Scanning the chain...", isBot: true }]);

  const handleChat = (e) => {
    e.preventDefault();
    if (!chatInput.trim()) return;
    setChatHistory([...chatHistory, { text: chatInput, isBot: false }]);
    setChatInput("");
    setTimeout(() => {
      setChatHistory(prev => [...prev, { text: "Scanning... My monocle sees bullish momentum!", isBot: true }]);
    }, 800);
  };

  return (
    <div className="min-h-screen">
      <GlobalStyles />
      
      {/* Sidebar Navigation */}
      <nav className="fixed left-0 top-0 h-full w-16 hover:w-64 bg-[#1A4D2E] border-r-4 border-[#D4AF37] transition-all duration-300 z-40 overflow-hidden group">
         <div className="p-4 flex flex-col gap-8 text-white font-bold whitespace-nowrap">
            <button onClick={() => setPage('home')} className="hover:text-[#D4AF37]">🏠 <span className="hidden group-hover:inline ml-4">Dashboard</span></button>
            <button onClick={() => setPage('club')} className="hover:text-[#D4AF37]">✨ <span className="hidden group-hover:inline ml-4">Alpha Club</span></button>
         </div>
      </nav>

      {/* Main Content Area */}
      <div className="pl-20 pr-4 pt-8">
        {page === 'home' ? (
          <div className="max-w-4xl mx-auto space-y-8">
            <div className="bg-white border-4 border-[#1A4D2E] p-8 rounded-lg shadow-retro text-center">
              <CuteAlphie />
              <h1 className="text-5xl font-['Pacifico'] text-[#1A4D2E] mb-2">Alphie</h1>
              <p className="bg-[#D4AF37] text-[#1A4D2E] inline-block px-4 py-1 font-bold">SYSTEM ONLINE</p>
            </div>

            <div className="grid md:grid-cols-2 gap-6">
              {/* Chat Box */}
              <div className="bg-white border-4 border-[#1A4D2E] rounded-lg shadow-retro flex flex-col h-96">
                <div className="bg-[#1A4D2E] text-[#D4AF37] p-2 font-bold">TERMINAL_LINK</div>
                <div className="flex-1 p-4 overflow-y-auto space-y-4">
                  {chatHistory.map((m, i) => (
                    <div key={i} className={`p-2 border-2 border-[#1A4D2E] rounded ${m.isBot ? 'bg-[#1A4D2E] text-[#D4AF37]' : 'bg-white'}`}>
                      {m.text}
                    </div>
                  ))}
                </div>
                <form onSubmit={handleChat} className="p-2 border-t-4 border-[#1A4D2E]">
                  <input 
                    value={chatInput} 
                    onChange={e => setChatInput(e.target.value)}
                    className="w-full p-2 outline-none font-bold" 
                    placeholder="Message Alphie..." 
                  />
                </form>
              </div>

              {/* Alpha Feed Mockup */}
              <div className="space-y-4">
                <h2 className="text-2xl font-bold border-b-4 border-[#D4AF37] inline-block">Live Feed</h2>
                {[1, 2, 3].map(i => (
                  <div key={i} className="bg-white border-4 border-[#1A4D2E] p-4 rounded shadow-retro hover:translate-x-1 transition-transform cursor-pointer">
                    <div className="text-xs font-bold text-[#D4AF37]">ETH_MAINNET</div>
                    <div className="font-bold">Project_Alpha_{i}: Volume Spike Detected</div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        ) : (
          <JoinClubPage />
        )}
      </div>
    </div>
  );
}
