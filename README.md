# MOVIMIENTO-DE-CARACTERES-POR-MEDIO-DE-COMAS
Las comas significan pies en alguna clase de idioma extraño
import React, { useState } from 'react';

type CharacterRange = {
  start: number;
  end: number;
  label: string;
};

const characterRanges: CharacterRange[] = [
  { start: 1, end: 500, label: '1 - 500' },
  { start: 501, end: 1000, label: '501 - 1000' },
  { start: 1001, end: 1500, label: '1001 - 1500' },
  { start: 1501, end: 2000, label: '1501 - 2000' },
  { start: 2001, end: 2022, label: '2001 - 2022' },
];

const CharacterSelectionApp: React.FC = () => {
  const [selectedRange, setSelectedRange] = useState<CharacterRange | null>(null);
  const [selectedComma, setSelectedComma] = useState<string>('');

  const handleRangeChange = (range: CharacterRange) => {
    setSelectedRange(range);
  };

  const handleCommaChange = (comma: string) => {
    setSelectedComma(comma);
  };

  const handleSave = () => {
    if (selectedRange && selectedComma) {
      alert(
        `Selected Range: ${selectedRange.label}, Selected Comma: ${selectedComma}`
      );
    } else {
      alert('Please select a range and a comma.');
    }
  };

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-gray-100 p-8">
      <h1 className="text-3xl font-semibold mb-8 text-gray-800">
        Character Selection
      </h1>

      <div className="bg-white shadow-md rounded-lg p-6 w-full max-w-md">
        <h2 className="text-xl font-medium mb-4 text-gray-700">
          Character Range
        </h2>
        <div className="space-y-2">
          {characterRanges.map((range) => (
            <button
              key={range.start}
              className={`block w-full text-left px-4 py-2 rounded-md transition-colors duration-200 ${
                selectedRange === range
                  ? 'bg-blue-500 text-white hover:bg-blue-600'
                  : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
              }`}
              onClick={() => handleRangeChange(range)}
            >
              {range.label}
            </button>
          ))}
        </div>

        <h2 className="text-xl font-medium mt-6 mb-4 text-gray-700">
          Comma Selection
        </h2>
        <div className="space-y-2">
          <button
            className={`block w-full text-left px-4 py-2 rounded-md transition-colors duration-200 ${
              selectedComma === ','
                ? 'bg-blue-500 text-white hover:bg-blue-600'
                : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
            }`}
            onClick={() => handleCommaChange(',')}
          >
            ,
          </button>
          <button
            className={`block w-full text-left px-4 py-2 rounded-md transition-colors duration-200 ${
              selectedComma === ',,'
                ? 'bg-blue-500 text-white hover:bg-blue-600'
                : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
            }`}
            onClick={() => handleCommaChange(',,')}
          >
            ,,
          </button>
        </div>

        <div className="mt-6 flex justify-end">
          <button
            className="bg-green-500 hover:bg-green-600 text-white font-semibold px-4 py-2 rounded-md transition-colors duration-200"
            onClick={handleSave}
          >
            Accept & Save
          </button>
        </div>
      </div>
    </div>
  );
};

export default CharacterSelectionApp;
