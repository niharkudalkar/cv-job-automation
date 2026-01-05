# CV-Based Job Application Automation

## Overview

An intelligent Python-based automation framework designed to streamline the job application process for professionals in India. This tool automates CV keyword extraction, job discovery across multiple platforms, resume tailoring, and application tracking.

### Key Features

✅ **CV Keyword Extraction** - Automatically parse and extract relevant skills, roles, and experience from your master resume

✅ **Multi-Platform Job Discovery** - Search across India's top job portals:
- LinkedIn
- Naukri.com
- Indeed India
- Glassdoor India
- Monster India

✅ **Intelligent Resume Tailoring** - Customize resume for each job posting with relevant keywords

✅ **Smart Cover Letter Generation** - Generate contextual cover letters for each application

✅ **Application Tracking** - Maintain comprehensive logs of all applications with follow-up dates

## Installation

### Prerequisites
- Python 3.7+
- pip (Python package manager)

### Setup

1. Clone the repository:
```bash
git clone https://github.com/niharkudalkar/cv-job-automation.git
cd cv-job-automation
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Prepare your master resume:
- Place your master resume file as `resume_master.docx` in the project root directory
- The script will use this as the base for tailored resumes

## Usage

### Basic Usage

```bash
python job_automation.py
```

### Workflow Steps

The automation follows a 6-step workflow:

**Step 1: Extract Keywords from CV**
- Parses your resume_master.docx file
- Extracts key skills, roles, and experience levels
- Returns structured keyword dictionary

**Step 2: Discover Job Opportunities**
- Searches multiple job boards using your extracted keywords
- Filters for India-based positions
- Returns list of matching opportunities

**Step 3: Tailor Resume**
- Customizes your master resume for each job posting
- Inserts relevant keywords and highlights
- Saves customized resume as separate file

**Step 4: Generate Cover Letter**
- Creates personalized cover letter based on job description
- Includes your professional summary and key qualifications
- Formatted and ready to send

**Step 5: Log Application**
- Records application details in `applications_log.json`
- Tracks company, role, submission date, and status
- Sets automatic follow-up reminders (7 days)

**Step 6: Summary Report**
- Generates summary of applications submitted
- Displays statistics and next steps

## Configuration

### Master Resume (resume_master.docx)
Ensure your master resume includes:
- Professional summary
- Key skills (clearly labeled)
- Work experience with quantifiable achievements
- Technical and soft skills
- Certifications and education

### Job Sites
Edit the `job_sites` dictionary in the script to add/remove job boards:
```python
job_sites = {
    "LinkedIn": "https://www.linkedin.com/jobs/search",
    "Naukri": "https://www.naukri.com",
    # Add more as needed
}
```

## Output Files

The script generates the following files:

- `Resume_[Company]_[Role].docx` - Tailored resume for each application
- `CoverLetter_[Company]_[Role].txt` - Generated cover letter
- `applications_log.json` - Master log of all applications

### Sample applications_log.json
```json
[
  {
    "date": "2024-01-05 15:30:45",
    "company": "TechCorp",
    "role": "Product Manager",
    "site": "LinkedIn",
    "url": "https://linkedin.com/jobs/...",
    "resume": "Resume_TechCorp_Product_Manager.docx",
    "cover_letter": "CoverLetter_TechCorp_Product_Manager.txt",
    "status": "Applied",
    "follow_up_date": "2024-01-12"
  }
]
```

## Requirements

- **python-docx** - For parsing and creating Word documents
- **requests** - For HTTP requests to job board APIs
- **python-dotenv** - For environment variable management
- **schedule** - For scheduling automated job runs

## Advanced Usage

### Scheduled Automation

To run the automation on a schedule (e.g., daily):

```python
import schedule
import time

schedule.every().day.at("09:00").do(main)

while True:
    schedule.run_pending()
    time.sleep(60)
```

### Custom Keywords

Modify the keywords dictionary in `extract_keywords_from_cv()` to focus on specific roles:

```python
keywords = {
    "roles": ["Product Manager", "Director", "Delivery Head"],
    "skills": ["Agile", "SaaS", "Team Management"],
    "experience_level": "Senior"
}
```

## Important Notes

⚠️ **API Integration**: Current implementation uses placeholder job data. For production use:
- Implement actual API integrations with job board APIs
- Use Selenium or BeautifulSoup for web scraping (where permitted)
- Implement rate limiting and ethical scraping practices
- Respect robots.txt and terms of service

⚠️ **Resume Upload**: Manual resume uploads may be required on some job portals

⚠️ **Cover Letters**: Review generated cover letters before submission

## Best Practices

1. **Test First** - Run on a small set of jobs before full automation
2. **Review Content** - Always review tailored resumes and cover letters
3. **Update Regularly** - Keep your master resume current
4. **Track Applications** - Monitor the applications_log.json file
5. **Follow-up** - Use the log to track follow-ups and applications status
6. **Personalize** - Add personal touches to cover letters when possible

## Troubleshooting

### FileNotFoundError: resume_master.docx
- Ensure resume_master.docx is in the project root directory
- Check the file name spelling and extension

### Module not found errors
- Run: `pip install -r requirements.txt`
- Ensure you're using Python 3.7+

### No jobs discovered
- Check your keyword extraction
- Verify job site URLs are correct and accessible
- Implement actual API connections

## Future Enhancements

- [ ] Integration with LinkedIn API for direct job discovery
- [ ] NLP-based keyword extraction from job descriptions
- [ ] Email integration for automatic applications
- [ ] Machine learning for job relevance scoring
- [ ] Desktop GUI interface
- [ ] Cloud deployment (AWS Lambda, Google Cloud Functions)
- [ ] Email notifications for application status
- [ ] Integration with ATS systems

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

**Nihar Kudalkar**
- GitHub: [@niharkudalkar](https://github.com/niharkudalkar)
- LinkedIn: [Nihar Kudalkar](https://linkedin.com/in/your-profile)

## Disclaimer

This tool is designed for personal use to streamline your job search. Always:
- Review all generated content before submission
- Respect job board terms of service
- Follow ethical web scraping practices
- Verify all information in applications is accurate

## Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing issues for solutions
- Provide detailed error messages and logs

---

**Last Updated**: January 5, 2024
**Version**: 1.0.0
