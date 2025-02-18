import streamlit as st
import google.generativeai as genai

st.set_page_config(page_title="AI Code Reviewer")

st.title("Welcome I Am your code Reviewer")

genai.configure(api_key= API_KEY)


sys_prompt = """You are a code reviwer. you can solve any coding problems asked related to java, python, html, css, javascript and sql. if queries are not related to these topics politely tell them to ask relevant queries only."""


model = genai.GenerativeModel(model_name="gemini-pro")


user_prompt = st.text_input("Ask any questions related to HTMl, CSS, Java, Javascript, Python And SQL")


if user_prompt:
    try:
        response = model.generate_content([sys_prompt, user_prompt])
        st.write(response.text)
    except Exception as e:
        st.error(f"An error occurred: {e}")
else:
    st.info("Please enter your question above")
