# quiz-project-start
Created with CodeSandbox

import React, { useState } from 'react';
import './StepSlider.css';

const StepSlider = () => {
  const [value, setValue] = useState(14000);

  const handleChange = (event) => {
    setValue(Number(event.target.value));
  };

  const marks = [
    {
      value: 14000,
      label: '₹14,000',
    },
    {
      value: 18000,
      label: '₹18,000',
    },
  ];

  return (
    <div className="slider-container">
      <div className="slider-header">
        <span>Select Value: </span>
        <span className="info-icon" title="Information about this slider">ℹ️</span>
      </div>
      <input
        type="range"
        min="14000"
        max="18000"
        step="4000"
        value={value}
        onChange={handleChange}
        className="slider"
      />
      <div className="slider-marks">
        {marks.map((mark) => (
          <span key={mark.value} className="slider-mark" style={{ left: `${((mark.value - 14000) / 4000) * 50}%` }}>
            {mark.label}
          </span>
        ))}
      </div>
      <div className="slider-values">
        <span>₹14,000</span>
        <span>₹18,000</span>
      </div>
      <div className="slider-value-display">
        ₹{value.toLocaleString()}
      </div>
    </div>
  );
};

export default StepSlider;



.slider-container {
  width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  background-color: #f9f9f9;
  text-align: center;
}

.slider-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.info-icon {
  cursor: pointer;
  font-size: 0.9em;
}

.slider {
  width: 100%;
  margin: 20px 0;
}

.slider-marks {
  position: relative;
  height: 20px;
}

.slider-mark {
  position: absolute;
  top: -20px;
  transform: translateX(-50%);
}

.slider-values {
  display: flex;
  justify-content: space-between;
  margin-top: -10px;
}

.slider-value-display {
  margin-top: 20px;
  font-size: 1.5em;
  font-weight: bold;
}
