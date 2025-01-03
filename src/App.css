import React, { useState } from 'react';
import axios from 'axios';
import { useSpeechSynthesis } from 'react-speech-kit';
import './App.css';

const App = () => {
  const [question, setQuestion] = useState('');
  const [guidanceAnswer, setGuidanceAnswer] = useState(null);
  const { speak } = useSpeechSynthesis();

  const handleInputChange = (event) => {
    setQuestion(event.target.value);
  };

  const handleSubmit = async () => {
    if (question) {
      try {
        const response = await axios.post('https://2owawgyt71.execute-api.us-east-1.amazonaws.com/dev/blog-generation', {
          blog_topic: question,
        });

        if (response.status === 200) {
          const data = response.data;
          const answer = data.places_content || 'No guidance found for your question, but keep seeking!';
          setGuidanceAnswer(answer);
        } else {
          alert(`Failed to retrieve guidance. Server responded with status code: ${response.status}`);
        }
      } catch (error) {
        console.error('Error fetching guidance:', error);
        alert('An error occurred while fetching guidance.');
      }
    } else {
      alert('Please enter a question before seeking guidance.');
    }
  };

  const handleSpeak = () => {
    if (guidanceAnswer) {
      speak({ text: guidanceAnswer });
    }
  };

  return (
    <div className="App">
      <header className="App-header">
        <h1>🙏 Ask Gita - Spiritual Insights</h1>
        <p>🙏 Dive deep into the wisdom of the Bhagavad Gita. Ask your questions and uncover spiritual insights to guide your journey.</p>
      </header>

      <div className="input-section">
        <input
          type="text"
          value={question}
          onChange={handleInputChange}
          placeholder="What spiritual question is on your mind today?"
        />
        <button onClick={handleSubmit}>Ask Gita for Guidance</button>
      </div>

      {guidanceAnswer && (
        <div className="answer-section">
          <h2>Here's the wisdom we found for you:</h2>
          <p>{guidanceAnswer}</p>
          <button onClick={handleSpeak}>🎧 Hear the Guidance</button>
        </div>
      )}

      <footer>
        <p>🙌 Powered by Ask Gita | Spiritual Guidance for Everyone 🙌</p>
      </footer>
    </div>
  );
};

export default App;
