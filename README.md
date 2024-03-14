# Build-mini---XSpellCheck-


The XSpellCheck is a React-based application designed for real-time spell-checking and auto-correction. It uses a custom dictionary to identify and suggest corrections for common typos and misspellings in user-entered text. The app focuses on improving user-written content by flagging the first detected misspelling and offering a correction. 

By Converting  followimng as  already have the class-component based implementation, must convert it into functional-component based implementation without changing its UI look and working.

import React from "react";

// Define a custom dictionary of words and their corrections
const customDictionary = {
  teh: "the",
  wrok: "work",
  fot: "for",
  exampl: "example",
};

class SpellCheckApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputText: "",
      suggestedText: "",
    };
  }

  handleInputChange = (e) => {
    const text = e.target.value;
    this.setState({ inputText: text });

    // Implement a basic spelling check and correction
    const words = text.split(" ");
    const correctedWords = words.map((word) => {
      const correctedWord = customDictionary[word.toLowerCase()];
      return correctedWord || word;
    });

    const correctedText = correctedWords.join(" ");

    // Set the suggested text (first corrected word)
    const firstCorrection = correctedWords.find(
      (word, index) => word !== words[index]
    );
    this.setState({ suggestedText: firstCorrection || "" });
  };

  render() {
    return (
      <div>
        <h1>Spell Check and Auto-Correction</h1>
        <textarea
          value={this.state.inputText}
          onChange={this.handleInputChange}
          placeholder="Enter text..."
          rows={5}
          cols={40}
        />
        {this.state.suggestedText && (
          <p>
            Did you mean: <strong>{this.state.suggestedText}</strong>?
          </p>
        )}
      </div>
    );
  }
}

export default SpellCheckApp;
