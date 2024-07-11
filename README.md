import streamlit as st
from datetime import datetime

# Function to determine the astrological sign
def get_astrological_sign(day, month):
    if month == 12:
        sign = 'Sagittarius' if (day < 22) else 'Capricorn'
    elif month == 1:
        sign = 'Capricorn' if (day < 20) else 'Aquarius'
    elif month == 2:
        sign = 'Aquarius' if (day < 19) else 'Pisces'
    elif month == 3:
        sign = 'Pisces' if (day < 21) else 'Aries'
    elif month == 4:
        sign = 'Aries' if (day < 20) else 'Taurus'
    elif month == 5:
        sign = 'Taurus' if (day < 21) else 'Gemini'
    elif month == 6:
        sign = 'Gemini' if (day < 21) else 'Cancer'
    elif month == 7:
        sign = 'Cancer' if (day < 23) else 'Leo'
    elif month == 8:
        sign = 'Leo' if (day < 23) else 'Virgo'
    elif month == 9:
        sign = 'Virgo' if (day < 23) else 'Libra'
    elif month == 10:
        sign = 'Libra' if (day < 23) else 'Scorpio'
    elif month == 11:
        sign = 'Scorpio' if (day < 22) else 'Sagittarius'
    return sign

# Function to provide descriptions and predictions for each astrological sign
def get_sign_prediction(sign):
    predictions = {
        "Aries": "Today, you will find new opportunities to showcase your leadership skills. Take the initiative!",
        "Taurus": "Patience will pay off. A financial gain or career advancement is on the horizon.",
        "Gemini": "Your curiosity will lead to new adventures. Embrace the changes coming your way.",
        "Cancer": "Focus on home and family. A loved one will bring you joy and comfort today.",
        "Leo": "Your charisma will attract positive attention. Use it to advance your personal goals.",
        "Virgo": "An organized approach will solve a lingering problem. Trust your analytical skills.",
        "Libra": "Balance is key today. Find harmony in your relationships and surroundings.",
        "Scorpio": "Passion and intensity will drive you. Channel this energy into your projects.",
        "Sagittarius": "Adventure awaits! Step out of your comfort zone and explore new horizons.",
        "Capricorn": "Hard work and dedication will be rewarded. Stay focused on your long-term goals.",
        "Aquarius": "Innovation and creativity will guide you. Think outside the box to find solutions.",
        "Pisces": "Your intuition is strong today. Trust your instincts and follow your heart."
    }
    return predictions.get(sign, "Prediction not available")

# Streamlit app
st.title("Astrological Prediction")

st.write("Enter your birthday to get your astrological prediction.")

day = st.number_input("Day", min_value=1, max_value=31)
month = st.number_input("Month", min_value=1, max_value=12)
year = st.number_input("Year", min_value=1900, max_value=datetime.now().year)

if st.button("Show Prediction"):
    try:
        # Validate date
        datetime(year, month, day)
        # Get astrological sign and prediction
        sign = get_astrological_sign(day, month)
        prediction = get_sign_prediction(sign)
        st.success(f"Your astrological sign is: {sign}\n\n{prediction}")
    except ValueError:
        st.error("Please enter a valid date.")
# mordenastrology
its all about astrology which can genetrated by the birthday ,month and year
