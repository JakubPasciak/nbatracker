
import React, { useState, useEffect } from 'react';
import axios from 'axios';
import './App.css';

const API_KEY = '1c54b650048a4424a7f8bb79a36cc9f3';

function App() {
  const [teams, setTeams] = useState([]);
  const [selectedTeam, setSelectedTeam] = useState(null);

  useEffect(() => {
    const fetchTeams = async () => {
      try {
        const response = await axios.get(`https://api.sportsdata.io/v3/nba/scores/json/teams?key=${API_KEY}`);
        setTeams(response.data);
      } catch (error) {
        console.error('Error fetching teams:', error);
      }
    };

    fetchTeams();
  }, []);

  const handleTeamClick = (team) => {
    setSelectedTeam(team);
  };

  const handleBackClick = () => {
    setSelectedTeam(null);
  };

  return (
    <div className="App">
      {!selectedTeam ? (
        <div className="team-grid">
          {teams.map((team) => (
            <div
              key={team.TeamID}
              className="team-tile"
              style={{ backgroundImage: `url(${team.WikipediaLogoUrl})`, backgroundColor: team.PrimaryColor }}
              onClick={() => handleTeamClick(team)}
            >
              <h3>{team.FullName}</h3>
            </div>
          ))}
        </div>
      ) : (
        <div className="team-info">
          <button onClick={handleBackClick}>Wróć</button>
          <h2>{selectedTeam.FullName}</h2>
          <img src={selectedTeam.WikipediaLogoUrl} alt={`${selectedTeam.FullName} logo`} />
          <p>Konferencja: {selectedTeam.Conference}</p>
          <p>Miasto: {selectedTeam.City}</p>
          <p>Dywizja: {selectedTeam.Division}</p>
        </div>
      )}
    </div>
  );
}

export default App;