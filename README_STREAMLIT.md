# Earthquake Impact Prediction System - Streamlit UI

A professional web-based interface for real-time earthquake impact prediction using machine learning.

## 📋 Features

- **🔮 Real-time Predictions**: Analyze earthquakes and get immediate risk assessments
- **📊 Model Analytics**: View feature importance and model performance metrics
- **📈 Scenario Analysis**: Explore predefined and custom earthquake scenarios
- **🎨 Interactive Visualizations**: Probability distributions, risk comparisons, and feature importance charts
- **📱 Responsive Design**: Works on desktop and mobile devices

## 🚀 Quick Start

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Run the Streamlit App

```bash
streamlit run earthquake_ui.py
```

The app will open automatically in your browser at `http://localhost:8501`

## 📖 How to Use

### Prediction Page (🔮)
1. **Enter Earthquake Parameters:**
   - Magnitude (Richter scale, 1-9)
   - Depth (0-700 km)
   - Community Decimal Intensity (CDI, 1-10)
   - Modified Mercalli Intensity (MMI, 1-10)
   - Significance Score (0-100)

2. **Click "Analyze Earthquake"** to get:
   - Alert level (Green/Yellow/Orange/Red)
   - Confidence percentage
   - Risk score and intensity metrics
   - Probability distribution chart

### Analysis Page (📊)
- View feature importance ranking
- See which features drive predictions
- Check model performance metrics
- Understand the machine learning model

### Scenarios Page (📈)
- Explore pre-configured earthquake scenarios:
  - Minor Shallow (Low Risk)
  - Moderate Deep (Medium Risk)
  - Strong Shallow (High Risk)
  - Major Shallow (Critical Risk)
- Compare risk levels visually
- Understand different earthquake types

### About Page (ℹ️)
- Learn about alert levels and recommendations
- Understand the ML model and features
- Review performance metrics

## 🎯 Alert Levels

| Level | Color | Risk | Recommendation |
|-------|-------|------|-----------------|
| 🟢 Green | #00b050 | Low | Monitor situation |
| 🟡 Yellow | #ffc000 | Moderate | Prepare & caution |
| 🟠 Orange | #ff7f00 | High | Alert & prepare |
| 🔴 Red | #c41e3a | Critical | Immediate evacuation |

## 📊 Model Specifications

- **Algorithm**: Gradient Boosting Classifier
- **Accuracy**: 90.08%
- **Cross-validation**: 87.05% ± 2.05%
- **Training Data**: 1,256 earthquake records
- **Features**: 8 (5 raw + 3 engineered)
- **Classes**: 4 alert levels

## 🔧 Features Explained

### Raw Features
- **Magnitude**: Energy released (Richter scale)
- **Depth**: Distance below surface (km)
- **CDI**: Community Decimal Intensity
- **MMI**: Modified Mercalli Intensity
- **Significance**: USGS importance score

### Engineered Features
- **Is Shallow**: Binary (1 if depth < 70km, else 0)
- **Intensity Score**: Average of CDI and MMI
- **Risk Score**: Magnitude × Intensity Score (most important predictor)

## 📦 File Structure

```
earthquake_ui.py          # Main Streamlit application
requirements.txt          # Python dependencies
README.md                 # This file
earthquake_training.py    # (Optional) Model training script
```

## 🌍 Integration with Jupyter Notebook

The Streamlit app uses a trained Gradient Boosting model. To use your trained model from the notebook:

1. **Save your model from the notebook:**
```python
import pickle
pickle.dump(gb_model, open('gb_model.pkl', 'wb'))
pickle.dump(scaler, open('scaler.pkl', 'wb'))
```

2. **Modify `earthquake_ui.py` to load your saved model:**
```python
@st.cache_resource
def load_model_and_scaler():
    model = pickle.load(open('gb_model.pkl', 'rb'))
    scaler = pickle.load(open('scaler.pkl', 'rb'))
    return model, scaler
```

## 🔌 Deployment Options

### Local Development
```bash
streamlit run earthquake_ui.py
```

### Deploy to Streamlit Cloud
1. Push code to GitHub
2. Visit https://share.streamlit.io
3. Connect GitHub repository
4. Deploy automatically

### Deploy to AWS/Azure/GCP
Use Docker containerization for production deployment.

## 📝 Environment Variables

Optional environment variables for production:
- `STREAMLIT_SERVER_PORT`: Port number (default: 8501)
- `STREAMLIT_SERVER_HEADLESS`: Run without UI (true/false)
- `STREAMLIT_LOGGER_LEVEL`: Logging level (debug/info/warning/error)

## 🐛 Troubleshooting

### Port Already in Use
```bash
streamlit run earthquake_ui.py --server.port 8502
```

### Module Not Found
```bash
pip install --upgrade -r requirements.txt
```

### Performance Issues
The model uses caching for fast predictions. Clear cache with:
```bash
streamlit cache clear
```

## 📚 Resources

- [Streamlit Documentation](https://docs.streamlit.io)
- [Scikit-learn ML Guide](https://scikit-learn.org)
- [USGS Earthquake Data](https://earthquake.usgs.gov)

## 📄 License

This project is for educational and research purposes.

## 👨‍💻 Support

For issues or questions:
1. Check the troubleshooting section above
2. Review Streamlit documentation
3. Verify all dependencies are installed correctly

---

**Build with Streamlit | Train with Scikit-learn | Deploy Anywhere**
