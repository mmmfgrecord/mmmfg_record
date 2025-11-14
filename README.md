# mmmfg_record
A full-featured React-based music distribution and record label platform. Artists can upload songs, track streams, manage profiles, and labels can oversee releases. Built with modern styling, analytics dashboards, and a professional UI
import React from 'react';

// Custom theme colors
const theme = {
  background: '#1A1A2E',
  card: '#162447',
  cardHighlight: '#1F4068',
  textPrimary: '#E43F5A',
  textSecondary: '#F0F0F0',
  button: '#E43F5A',
  buttonHover: '#FF5964'
};

// --- ArtistProfile Component ---
function ArtistProfile() {
  const artist = {
    name: 'Melo Drip',
    genre: 'Amapiano',
    country: 'Nigeria',
    bio: 'Rising Amapiano star blending Afrobeat rhythms with modern electronic vibes.',
    social: { instagram: '@melodrip', twitter: '@melodrip', youtube: 'youtube.com/melodrip' },
    releases: [
      { title: 'Nightfall Beat', streams: 1240000 },
      { title: 'Sunrise Vibes', streams: 2120000 }
    ]
  };

  return (
    <div className="p-6 max-w-3xl mx-auto" style={{background: theme.background, fontFamily: 'Poppins, sans-serif'}}>
      <h1 className="text-4xl font-extrabold mb-4" style={{color: theme.textPrimary}}>Artist Profile</h1>
      <div className="flex items-center space-x-4 mb-6">
        <div className="w-24 h-24" style={{background: theme.card, borderRadius: '50%', border: `2px solid ${theme.textPrimary}`}}></div>
        <div>
          <h2 className="text-2xl font-bold" style={{color: theme.textSecondary}}>{artist.name}</h2>
          <p style={{color: theme.textSecondary}}>{artist.genre} • {artist.country}</p>
        </div>
      </div>
      <div className="mb-6">
        <h3 className="text-xl font-semibold mb-2" style={{color: theme.textPrimary}}>Bio</h3>
        <p style={{color: theme.textSecondary}}>{artist.bio}</p>
      </div>
      <div className="mb-6">
        <h3 className="text-xl font-semibold mb-2" style={{color: theme.textPrimary}}>Social Links</h3>
        <div className="space-y-2" style={{color: theme.textSecondary}}>
          <p>Instagram: {artist.social.instagram}</p>
          <p>Twitter: {artist.social.twitter}</p>
          <p>YouTube: {artist.social.youtube}</p>
        </div>
      </div>
      <div>
        <h3 className="text-xl font-semibold mb-2" style={{color: theme.textPrimary}}>Releases</h3>
        <div className="grid grid-cols-2 gap-4">
          {artist.releases.map((song, idx) => (
            <div key={idx} className="p-4 rounded-xl" style={{background: theme.cardHighlight}}>
              <div className="w-full h-32" style={{background: theme.card, borderRadius: '0.5rem', marginBottom: '0.5rem'}}></div>
              <p className="font-semibold" style={{color: theme.textSecondary}}>{song.title}</p>
              <p style={{color: theme.textSecondary, fontSize: '0.875rem'}}>Streams: {song.streams.toLocaleString()}</p>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}

// --- SongUpload Component ---
function SongUpload() {
  const sampleUploads = [
    { title: 'Morning Glow', artist: 'Kai Rivera', genre: 'Indie Pop', date: '2025-11-01' },
    { title: 'Afro Sunrise', artist: 'Luna Waves', genre: 'Afrobeats', date: '2025-10-28' }
  ];

  return (
    <div className="p-6 max-w-3xl mx-auto" style={{background: theme.background, fontFamily: 'Poppins, sans-serif'}}>
      <h1 className="text-4xl font-extrabold mb-6" style={{color: theme.textPrimary}}>Upload New Release</h1>
      <div className="mb-6">
        <label className="block mb-2 font-semibold" style={{color: theme.textSecondary}}>Upload Audio (MP3/WAV)</label>
        <input type="file" accept="audio/*" className="w-full p-3 rounded-xl" style={{background: theme.card, color: theme.textSecondary}} />
      </div>
      <div className="mb-6">
        <label className="block mb-2 font-semibold" style={{color: theme.textSecondary}}>Upload Cover Art</label>
        <input type="file" accept="image/*" className="w-full p-3 rounded-xl" style={{background: theme.card, color: theme.textSecondary}} />
      </div>
      <div className="grid grid-cols-1 gap-4 mb-6">
        <input type="text" placeholder="Song Title" className="w-full p-3 rounded-xl" style={{background: theme.card, color: theme.textSecondary}} />
        <input type="text" placeholder="Primary Artist" className="w-full p-3 rounded-xl" style={{background: theme.card, color: theme.textSecondary}} />
        <input type="text" placeholder="Genre" className="w-full p-3 rounded-xl" style={{background: theme.card, color: theme.textSecondary}} />
        <input type="date" className="w-full p-3 rounded-xl" style={{background: theme.card, color: theme.textSecondary}} />
      </div>
      <div className="mb-6">
        <h3 className="text-xl font-semibold mb-2" style={{color: theme.textPrimary}}>Select Platforms</h3>
        <div className="grid grid-cols-2 gap-4" style={{color: theme.textSecondary}}>
          <label><input type="checkbox" /> Spotify</label>
          <label><input type="checkbox" /> Apple Music</label>
          <label><input type="checkbox" /> Boomplay</label>
          <label><input type="checkbox" /> YouTube Music</label>
          <label><input type="checkbox" /> TikTok</label>
          <label><input type="checkbox" /> Amazon Music</label>
        </div>
      </div>
      <button className="w-full p-3 rounded-xl font-bold transition" style={{background: theme.button, color: '#fff'}} onMouseOver={e => e.currentTarget.style.background = theme.buttonHover} onMouseOut={e => e.currentTarget.style.background = theme.button}>Submit Release</button>
      <div className="mt-8">
        <h3 className="text-2xl font-semibold mb-2" style={{color: theme.textPrimary}}>Recent Uploads</h3>
        <ul className="space-y-2" style={{color: theme.textSecondary}}>
          {sampleUploads.map((upload, idx) => (
            <li key={idx}>{upload.title} by {upload.artist} ({upload.genre}) - {upload.date}</li>
          ))}
        </ul>
      </div>
    </div>
  );
}

// --- Main App Component ---
export default function App() {
  return (
    <div style={{fontFamily: 'Poppins, sans-serif', backgroundColor: theme.background, minHeight: '100vh', color: theme.textSecondary, paddingBottom: '2rem'}}>
      <h1 style={{textAlign: 'center', padding: '2rem', color: theme.textPrimary}}>MMMFG RECORD Platform</h1>
      <ArtistProfile />
      <SongUpload />
    </div>
  );
}
