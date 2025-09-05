---
title: Delphi Risk Assessment Mockups
date: 2025-01-01
summary: Interactive visualizations and interfaces for expert risk assessment in AI governance research
draft: false
---

# Delphi Risk Assessment Mockups

This collection demonstrates different approaches to visualizing and collecting expert assessments of AI risks. Each example explores different aspects of risk communication and data collection for Delphi method research.

## Examples Overview

### [Example 1: Risk Exceedance Curve](example1/)
**Risk 3.1 - False or Misleading Information Exceedance Probability Curve**
Interactive probability curve showing likelihood of exceeding different severity thresholds with detailed data breakdown.

### [Example 2: Probability Bands Distribution](example2/)  
**Risk 3.1 - Probability Distribution by Severity Level**
Horizontal band visualization showing probability distribution across all severity categories with interactive tooltips.

### [Example 3: Comparative Risk Ranking](example3/)
**AI Risk Comparative Ranking by Moderate Harm Probability** 
Horizontal bar chart ranking all risks by probability of moderate or worse outcomes.

### [Example 4: Risk Progression Analysis](example4/)
**Multi-Risk Severity Progression with Interactive Selection**
Line chart showing probability trajectories across severity levels for all risks with responsive design.

### [Example 5: Expert Survey Interface](example5/)
**Interactive Risk Assessment Data Collection Tool**
Survey-style interface for experts to input probability assessments with real-time validation and interpretation.

## Design Principles

- **Cumulative Probability Logic**: All visualizations respect that P(≥Severe) ≤ P(≥Moderate) ≤ P(≥Limited)
- **Responsive Design**: All examples scale appropriately across viewport sizes
- **Interactive Feedback**: Users receive immediate visual and textual feedback on their inputs
- **Validation**: Built-in logical consistency checks for expert assessments
- **Accessibility**: Clear typography, sufficient contrast, and intuitive navigation

## Technical Implementation

- **Chart.js**: Used for responsive, interactive visualizations
- **Vanilla JavaScript**: Clean, dependency-minimal implementations
- **CSS Grid/Flexbox**: Modern responsive layout techniques
- **Progressive Enhancement**: Functional without JavaScript, enhanced with it

## Risk Categories

The examples focus on AI risks across four main domains:

1. **Bias & Fairness (1.x)**: Discrimination, toxic content, unequal performance
2. **Privacy & Security (2.x)**: Data breaches, system vulnerabilities  
3. **Misinformation (3.x)**: False information, ecosystem pollution
4. **Malicious Actors (4.x)**: Disinformation campaigns, cyberattacks, fraud

---

*These mockups support research into expert elicitation methods for AI risk assessment and governance policy development.*