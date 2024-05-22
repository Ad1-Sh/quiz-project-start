# quiz-project-start
Created with CodeSandbox

import React, { useState } from 'react';
import { Slider, Typography, Box, Tooltip } from '@mui/material';
import InfoOutlinedIcon from '@mui/icons-material/InfoOutlined';

const ValueLabelComponent = (props) => {
  const { children, value } = props;

  return (
    <Tooltip enterTouchDelay={0} placement="top" title={value}>
      {children}
    </Tooltip>
  );
};

const StepSlider = () => {
  const [value, setValue] = useState(14000);

  const handleChange = (event, newValue) => {
    setValue(newValue);
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
    <Box sx={{ width: 300, margin: '0 auto', mt: 5 }}>
      <Box display="flex" alignItems="center" justifyContent="space-between">
        <Typography variant="body1">Select Value:</Typography>
        <Tooltip title="Information about this slider" placement="top">
          <InfoOutlinedIcon fontSize="small" />
        </Tooltip>
      </Box>
      <Slider
        value={value}
        onChange={handleChange}
        aria-labelledby="discrete-slider"
        step={null}
        marks={marks}
        min={14000}
        max={18000}
        valueLabelDisplay="auto"
        ValueLabelComponent={ValueLabelComponent}
      />
      <Box display="flex" justifyContent="space-between">
        <Typography variant="body2">₹14,000</Typography>
        <Typography variant="body2">₹18,000</Typography>
      </Box>
      <Box mt={2} textAlign="center">
        <Typography variant="h5">₹{value.toLocaleString()}</Typography>
      </Box>
    </Box>
  );
};

export default StepSlider;
