import streamlit as st
from groq import Groq
st.set_page_config(page_title = "PLACEMENT PRECTICE", layout = 'centered')
st.title( "AI_ASSISTANT INTERVIEWER")
st.caption("practice and prepare for your Interviews")
try:
client = Groq(api_key = st.secrets("GROQ_API_KEY"))
except (keyError,FileNotFound):
st.error("API Key is missing.Add it in Advanced settings")
st.stop()
