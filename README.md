# Resume Application Tracking System (ATS) using Google Gemini 1.5 Flash

## Aim
The goal of this project is to develop a smart, AI-powered Applicant Tracking System (ATS) that evaluates resumes based on job descriptions using Google Gemini 1.5. The system assists users by offering insights into resume-job matching and suggestions for improvement, tailored for competitive job markets in technical fields like software engineering, data science, and big data engineering.

## Methodology
The project utilizes the following components and tools:

1. **Streamlit**: A framework used to build the web application interface.
2. **Google Gemini 1.5**: A generative AI model for analyzing resume and job description content and providing relevant feedback.
3. **PyPDF2**: A library to extract text content from uploaded PDF resumes.
4. **Python Dotenv**: For loading environment variables (API keys, etc.).
5. **Custom Prompt**: The AI is prompted to act as an experienced ATS and provide detailed resume evaluations based on job description matching, missing keywords, and profile summaries.

### Process
1. **User Interface**: 
   - The user uploads their resume in PDF format and pastes a job description into a text area.
   
2. **Resume Text Extraction**: 
   - The PDF resume is processed using `PyPDF2` to extract text from all pages.

3. **Generative AI Processing**: 
   - The extracted resume text and job description are passed into a predefined input prompt designed to simulate an ATS. Google Gemini 1.5 evaluates the resume based on the job description.

4. **Response Parsing**: 
   - The system returns a JSON-like string, containing:
     - **Job Description Match (%)**: A percentage score of how well the resume fits the job description.
     - **Missing Keywords**: Keywords that are essential but not present in the resume.
     - **Profile Summary**: A brief assessment of the overall quality and relevance of the resume for the job.

### Input Prompt
The prompt used by the AI for evaluation is structured as follows:
```python
input_prompt = """
Hey Act Like a skilled or very experienced ATS (Application Tracking System)
with a deep understanding of tech field, software engineering, data science, data analyst
and big data engineer. Your task is to evaluate the resume based on the given job description.
You must consider the job market is very competitive and you should provide
best assistance for improving the resumes. Assign the percentage Matching based 
on JD and
the missing keywords with high accuracy
resume: {text}
description: {jd}

I want the response in one single string having the structure
{"JD Match": "%", "MissingKeywords": [], "Profile Summary": ""}
'''
## Evaluation Metrics
The project evaluates the resumes based on:

1. **JD Match (%)**: The similarity between the resume and the job description, providing an overall fit score.
2. **Missing Keywords**: Identifying crucial keywords missing in the resume that are present in the job description.
3. **Profile Summary**: A qualitative assessment that offers suggestions for improvement based on the job market demands.

## Results
The system provides the following output upon submitting a resume and job description:

A JSON string showing the matching percentage, missing keywords, and profile summary.

### Example Output:
```json
{
    "JD Match": "85%",
    "MissingKeywords": ["Python", "SQL", "Machine Learning"],
    "Profile Summary": "The resume matches the job description well, but is missing key skills such as Python, SQL, and Machine Learning. Consider adding more details about your experience in these areas."
}


## Conclusion
This project successfully creates a user-friendly, AI-powered ATS system that helps individuals optimize their resumes for job descriptions. Google Gemini 1.5 provides accurate and insightful feedback, making it a valuable tool for job seekers, particularly in highly competitive technical fields.

## Future Work
1. **Multilingual Support**: Expanding the system to support resumes and job descriptions in multiple languages.
2. **Integration with Job Boards**: Automating the process of resume evaluation by integrating the ATS with popular job boards.
3. **Improved Matching Algorithm**: Further refining the matching percentage by incorporating advanced NLP techniques to consider synonyms and broader skill sets.
4. **Profile Benchmarking**: Allowing users to benchmark their resumes against other candidates in the same field.
5. **Resume Formatting Suggestions**: Providing feedback not only on content but also on resume format and structure to enhance readability and ATS-friendliness.

## How to Run

### Prerequisites
1. Python 3.x
2. API key for Google Gemini (add this to a `.env` file)
3. Required Python packages from `requirements.txt`

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/username/Resume-Application-Tracking-System-ATS-using-Google-Gemini-1.5-flash.git
   cd Resume-Application-Tracking-System-ATS-using-Google-Gemini-1.5-flash
2. Install the dependencies:
    ```bash
    pip install -r requirements.txt
3. Add your Google Gemini API key to a .env file:
    ```bash
    GOOGLE_API_KEY=your_google_gemini_api_key
4. Run the application:
    ```bash
     streamlit run app.py

