import os
import streamlit as st
from gtts import gTTS
import IPython.display as ipd
import google.generativeai as genai
import pandas as pd

# Read employee data from Excel
df = pd.read_excel('emp1.xlsx')



# Set up Google API key
os.environ['GOOGLE_API_KEY'] = "AIzaSyDLPW9L43--3z8rLcffglMQeUcSaXEwqdQ"
genai.configure(api_key=os.environ['GOOGLE_API_KEY'])

# Page configuration
st.set_page_config(
    page_title="Bishnu Haldar",
    page_icon="🤖",
    layout="wide"
)

# App title and description
st.title("TalentFinder🚀")

prompt1 = """Hey, you are a consultant for my 
company. The following are the employees of my company along with their skillsets:"""

employee_data_dict = df.set_index('Employee').to_dict(orient='index')

prompt2 = "Hey, who is suitable for the following task -"

user_input = st.text_input("Skill")

prompt3 = "Tell only the name of the employee ."

final_prompt = f"{prompt1}\n{employee_data_dict}\n{prompt2}{user_input} {prompt3}"

# Button to generate content
if st.button("Find"):
    # Create generative model
    model = genai.GenerativeModel('gemini-pro')

    # Generate content based on user input
    response = model.generate_content(final_prompt)

    # Display the generated content
    st.header(response.text)

# Footer and attribution
st.markdown("---")
st.write("Developed by Bishnu")

# Add a background image or color to the app
st.markdown(
    """
    <style>
    body {
        background-color: #f1f1f1;
    }
    </style>
    """,
    unsafe_allow_html=True
)
