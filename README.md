<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HealthInsight - Smart Medication Finder</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --primary: #0066cc;
            --primary-light: #e6f2ff;
            --secondary: #004d99;
            --accent: #ff6600;
            --light: #f8f9fa;
            --dark: #212529;
            --gray: #6c757d;
            --light-gray: #e9ecef;
            --success: #28a745;
            --warning: #ffc107;
            --danger: #dc3545;
            --border-radius: 12px;
            --box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: #f5f7ff;
            color: var(--dark);
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 20px 0;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            border-radius: 0 0 var(--border-radius) var(--border-radius);
            margin-bottom: 2rem;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo img {
            height: 40px;
            border-radius: 50%;
        }

        .logo h1 {
            font-size: 1.5rem;
            font-weight: 700;
            margin: 0;
        }

        .tagline {
            font-style: italic;
            opacity: 0.9;
            font-size: 0.9rem;
            margin-top: 5px;
        }

        .profile-btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            padding: 8px 16px;
            border-radius: 50px;
            display: flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .profile-btn:hover {
            background: rgba(255, 255, 255, 0.3);
        }

        .progress-bar {
            display: flex;
            justify-content: space-between;
            margin: 30px 0;
            position: relative;
        }

        .progress-step {
            display: flex;
            flex-direction: column;
            align-items: center;
            z-index: 1;
            flex: 1;
        }

        .step-number {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: var(--light-gray);
            color: var(--gray);
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            margin-bottom: 10px;
            transition: all 0.3s ease;
        }

        .step-label {
            font-size: 0.9rem;
            color: var(--gray);
            text-align: center;
            max-width: 100px;
        }

        .progress-bar::before {
            content: '';
            position: absolute;
            top: 20px;
            left: 0;
            right: 0;
            height: 4px;
            background-color: var(--light-gray);
            z-index: 0;
        }

        .progress-bar .active .step-number {
            background-color: var(--primary);
            color: white;
            box-shadow: 0 4px 8px rgba(0, 102, 204, 0.3);
        }

        .progress-bar .completed .step-number {
            background-color: var(--success);
            color: white;
        }

        .form-section {
            background-color: white;
            border-radius: var(--border-radius);
            padding: 30px;
            box-shadow: var(--box-shadow);
            margin-bottom: 30px;
            display: none;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .form-section.active {
            display: block;
        }

        h2 {
            color: var(--primary);
            margin-top: 0;
            margin-bottom: 1.5rem;
            font-size: 1.5rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        h2 i {
            font-size: 1.2rem;
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--dark);
        }

        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid var(--light-gray);
            border-radius: var(--border-radius);
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        .form-control:focus {
            border-color: var(--primary);
            outline: none;
            box-shadow: 0 0 0 3px rgba(0, 102, 204, 0.2);
        }

        .checkbox-group {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
        }

        .checkbox-item {
            flex: 1 1 200px;
            display: flex;
            align-items: center;
            background: var(--light);
            padding: 12px 15px;
            border-radius: var(--border-radius);
            transition: all 0.3s ease;
        }

        .checkbox-item:hover {
            background: var(--primary-light);
        }

        .checkbox-item input {
            width: auto;
            margin-right: 10px;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            padding: 12px 24px;
            border-radius: var(--border-radius);
            font-size: 1rem;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            border: none;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
            box-shadow: 0 4px 12px rgba(0, 102, 204, 0.2);
        }

        .btn-primary:hover {
            background: var(--secondary);
            transform: translateY(-2px);
            box-shadow: 0 6px 16px rgba(0, 102, 204, 0.3);
        }

        .btn-outline {
            background: transparent;
            color: var(--primary);
            border: 1px solid var(--primary);
        }

        .btn-outline:hover {
            background: var(--primary-light);
        }

        .btn-group {
            display: flex;
            justify-content: space-between;
            margin-top: 30px;
        }

        .results-container {
            display: none;
        }

        .medication-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: var(--box-shadow);
            border-left: 4px solid var(--primary);
        }

        .medication-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 15px;
        }

        .medication-name {
            font-size: 1.3rem;
            color: var(--primary);
            margin: 0;
        }

        .medication-type {
            display: inline-block;
            padding: 4px 10px;
            background-color: var(--primary-light);
            color: var(--primary);
            border-radius: 50px;
            font-size: 0.8rem;
            font-weight: 500;
        }

        .medication-details {
            margin-bottom: 15px;
        }

        .detail-row {
            display: flex;
            margin-bottom: 8px;
        }

        .detail-label {
            font-weight: 500;
            min-width: 120px;
            color: var(--gray);
        }

        .detail-value {
            flex: 1;
        }

        .warning {
            color: var(--danger);
            font-weight: 600;
        }

        .loading-spinner {
            display: none;
            text-align: center;
            padding: 30px;
        }

        .spinner {
            width: 40px;
            height: 40px;
            border: 4px solid var(--primary-light);
            border-top: 4px solid var(--primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto 15px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .disclaimer {
            background: var(--light);
            padding: 20px;
            border-radius: var(--border-radius);
            margin-top: 30px;
            font-size: 0.9rem;
            color: var(--gray);
        }

        .disclaimer strong {
            color: var(--danger);
        }

        footer {
            text-align: center;
            padding: 30px 0;
            color: var(--gray);
            font-size: 0.9rem;
            margin-top: 50px;
        }

        @media (max-width: 768px) {
            .container {
                padding: 15px;
            }

            .header-content {
                flex-direction: column;
                gap: 15px;
            }

            .progress-bar {
                flex-wrap: wrap;
                gap: 15px;
            }

            .progress-step {
                flex: 0 0 calc(50% - 15px);
            }

            .progress-bar::before {
                display: none;
            }

            .form-section {
                padding: 20px;
            }

            .checkbox-item {
                flex: 1 1 100%;
            }

            .btn-group {
                flex-direction: column;
                gap: 10px;
            }

            .btn {
                width: 100%;
            }

            .medication-header {
                flex-direction: column;
                gap: 10px;
            }

            .detail-row {
                flex-direction: column;
                gap: 5px;
            }

            .detail-label {
                min-width: 100%;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="header-content">
            <div class="logo">
                <img src="https://via.placeholder.com/40" alt="HealthInsight Logo">
                <div>
                    <h1>Health-Insight</h1>
                    <p class="tagline">Smart medication recommendations powered by Drugs.com</p>
                </div>
            </div>
            <button class="profile-btn" id="profileBtn">
                <i class="fas fa-user"></i>
                <a href="pp.html"><span>Profile</span></a>
            </button>
        </div>
    </header>

    <main class="container">
        <div class="progress-bar">
            <div class="progress-step active" data-step="1">
                <div class="step-number">1</div>
                <div class="step-label">Symptoms</div>
            </div>
            <div class="progress-step" data-step="2">
                <div class="step-number">2</div>
                <div class="step-label">Health History</div>
            </div>
            <div class="progress-step" data-step="3">
                <div class="step-number">3</div>
                <div class="step-label">Medication Results</div>
            </div>
        </div>
        
        <form id="medicationForm">
            <!-- Symptoms Section -->
            <div class="form-section active" id="symptoms-section">
                <h2><i class="fas fa-thermometer-half"></i> What symptoms are you experiencing?</h2>
                
                <div class="form-group">
                    <label>Primary Symptom</label>
                    <select class="form-control" id="primarySymptom" required>
                        <option value="">Select your main symptom</option>
                        <option value="headache">Headache</option>
                        <option value="fever">Fever</option>
                        <option value="cough">Cough</option>
                        <option value="sore throat">Sore Throat</option>
                        <option value="nasal congestion">Nasal Congestion</option>
                        <option value="body aches">Body Aches</option>
                        <option value="heartburn">Heartburn</option>
                        <option value="diarrhea">Diarrhea</option>
                        <option value="constipation">Constipation</option>
                        <option value="rash">Skin Rash</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label>Additional Symptoms (select all that apply)</label>
                    <div class="checkbox-group">
                        <label class="checkbox-item">
                            <input type="checkbox" name="symptoms" value="cold"> Cold
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="symptoms" value="chills"> Chills
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="symptoms" value="fatigue"> Fatigue
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="symptoms" value="nausea"> Nausea
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="symptoms" value="dizziness"> Dizziness
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="symptoms" value="sneezing"> Sneezing
                        </label>
                    </div>
                </div>
                
                <div class="form-group">
                    <label>How long have you had these symptoms?</label>
                    <select class="form-control" id="symptomDuration" required>
                        <option value="">Select duration</option>
                        <option value="less than 24 hours">Less than 24 hours</option>
                        <option value="1-3 days">1-3 days</option>
                        <option value="4-7 days">4-7 days</option>
                        <option value="1-2 weeks">1-2 weeks</option>
                        <option value="over 2 weeks">Over 2 weeks</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label>Symptom Severity</label>
                    <select class="form-control" id="symptomSeverity" required>
                        <option value="">Select severity</option>
                        <option value="mild">Mild - Annoying but doesn't interfere with daily activities</option>
                        <option value="moderate">Moderate - Limits some daily activities</option>
                        <option value="severe">Severe - Prevents most daily activities</option>
                    </select>
                </div>
                
                <div class="btn-group">
                    <button type="button" class="btn btn-outline" disabled>
                        <i class="fas fa-arrow-left"></i> Previous
                    </button>
                    <button type="button" class="btn btn-primary next-btn">
                        Next <i class="fas fa-arrow-right"></i>
                    </button>
                </div>
            </div>
            
            <!-- Health History Section -->
            <div class="form-section" id="health-section">
                <h2><i class="fas fa-medkit"></i> Your Health History</h2>
                
                <div class="form-group">
                    <label>Age</label>
                    <input type="number" class="form-control" id="age" min="1" max="120" required>
                </div>
                
                <div class="form-group">
                    <label>Gender</label>
                    <select class="form-control" id="gender" required>
                        <option value="">Select gender</option>
                        <option value="male">Male</option>
                        <option value="female">Female</option>
                        <option value="other">Other/Prefer not to say</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label>Do you have any of these medical conditions? (select all that apply)</label>
                    <div class="checkbox-group">
                        <label class="checkbox-item">
                            <input type="checkbox" name="conditions" value="high blood pressure"> High Blood Pressure
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="conditions" value="diabetes"> Diabetes
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="conditions" value="heart disease"> Heart Disease
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="conditions" value="liver disease"> Liver Disease
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="conditions" value="kidney disease"> Kidney Disease
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="conditions" value="asthma"> Asthma
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="conditions" value="pregnant"> Pregnant or Breastfeeding
                        </label>
                        <label class="checkbox-item">
                            <input type="checkbox" name="conditions" value="none"> None of the above
                        </label>
                    </div>
                </div>
                
                <div class="form-group">
                    <label>Are you currently taking any medications? (please list)</label>
                    <textarea class="form-control" id="currentMeds" rows="3" placeholder="e.g., Lisinopril 10mg daily, Metformin 500mg twice daily"></textarea>
                </div>
                
                <div class="form-group">
                    <label>Do you have any known allergies to medications?</label>
                    <textarea class="form-control" id="allergies" rows="2" placeholder="e.g., Penicillin causes rash"></textarea>
                </div>
                
                <div class="btn-group">
                    <button type="button" class="btn btn-outline prev-btn">
                        <i class="fas fa-arrow-left"></i> Previous
                    </button>
                    <button type="button" class="btn btn-primary" id="search-btn">
                        <i class="fas fa-search"></i> Search Medications
                    </button>
                </div>
            </div>
            
            <!-- Results Section -->
            <div class="form-section" id="results-section">
                <h2><i class="fas fa-pills"></i> Medication Recommendations</h2>
                
                <div class="loading-spinner" id="loadingSpinner">
                    <div class="spinner"></div>
                    <p>Searching for medication recommendations based on your symptoms...</p>
                </div>
                
                <div class="results-container" id="resultsContainer">
                    <div id="medicationResults"></div>
                    
                    <div class="disclaimer">
                        <p><strong>Disclaimer:</strong> These medication recommendations are provided for informational purposes only and do not constitute medical advice. Always consult with a qualified healthcare provider before starting any new medication.</p>
                        <p>Results are powered by Drugs.com's database and are not endorsed by HealthInsight.</p>
                    </div>
                </div>
                
                <div class="btn-group">
                    <button type="button" class="btn btn-outline prev-btn">
                        <i class="fas fa-arrow-left"></i> Previous
                    </button>
                    <button type="button" class="btn btn-primary" id="new-search-btn">
                        <i class="fas fa-redo"></i> New Search
                    </button>
                    <button type="button" class="btn btn-outline prev-btn" id="print-btn">
                        <i class="fas fa-arrow-right"></i>Print Recommendations
                    </button>
                </div>
            </div>
        </form>
    </main>
    
    <footer>
        <div class="container">
            <p>HealthInsight &copy; 2025 | This tool is for educational purposes only | Powered by Drugs.com API</p>
        </div>
    </footer>

    <script>
    document.addEventListener('DOMContentLoaded', function () {
        // Form navigation
        const formSections = document.querySelectorAll('.form-section');
        const progressSteps = document.querySelectorAll('.progress-step');
        const nextButtons = document.querySelectorAll('.next-btn');
        const prevButtons = document.querySelectorAll('.prev-btn');
        const searchButton = document.getElementById('search-btn');
        const newSearchButton = document.getElementById('new-search-btn');
        const loadingSpinner = document.getElementById('loadingSpinner');
        const resultsContainer = document.getElementById('resultsContainer');
        const medicationResults = document.getElementById('medicationResults');
        const printButton = document.getElementById('print-btn');

        let currentSection = 0;

        // Next button click handler
        nextButtons.forEach(button => {
            button.addEventListener('click', function () {
                if (validateSection(currentSection)) {
                    navigateToSection(currentSection + 1);
                }
            });
        });

        // Previous button click handler
        prevButtons.forEach(button => {
            button.addEventListener('click', function () {
                navigateToSection(currentSection - 1);
            });
        });

        // Search button click handler
        searchButton.addEventListener('click', function () {
            if (validateSection(currentSection)) {
                navigateToSection(currentSection + 1);
                searchDrugsCom(); // Make sure this function exists elsewhere in your code
            }
        });

        // New search button click handler
        newSearchButton.addEventListener('click', function () {
            navigateToSection(0);
            document.getElementById('medicationForm').reset();
            medicationResults.innerHTML = '';

            // Reset progress steps
            progressSteps.forEach(step => {
                step.classList.remove('completed');
                if (step.dataset.step === "1") {
                    step.classList.add('active');
                } else {
                    step.classList.remove('active');
                }
            });
        });

        // ✅ Print only the active form section
        printButton.addEventListener('click', function () {
            const activeSection = document.querySelector('.form-section.active');

            if (!activeSection) {
                alert('No section is currently active to print.');
                return;
            }

            const originalContent = document.body.innerHTML;
            const sectionContent = activeSection.innerHTML;

            const printHTML = `
                <html>
                <head>
                    <title>Print</title>
                    <style>
                        body { font-family: Arial, sans-serif; padding: 20px; }
                        .form-section { display: block; }
                        button, .next-btn, .prev-btn, .progress-bar, .header, .footer { display: none; }
                    </style>
                </head>
                <body>
                    ${sectionContent}
                </body>
                </html>
            `;

            const printWindow = window.open('', '_blank');
            printWindow.document.write(printHTML);
            printWindow.document.close();
            printWindow.focus();
            printWindow.print();
            printWindow.close();
        });

        // Navigate to specific section
        function navigateToSection(sectionIndex) {
            formSections[currentSection].classList.remove('active');
            progressSteps[currentSection].classList.remove('active');

            currentSection = sectionIndex;

            formSections[currentSection].classList.add('active');
            progressSteps[currentSection].classList.add('active');

            // Mark previous steps as completed
            for (let i = 0; i < sectionIndex; i++) {
                progressSteps[i].classList.add('completed');
            }
        }

        // Validate current form section
        function validateSection(sectionIndex) {
            const currentSection = formSections[sectionIndex];
            const requiredInputs = currentSection.querySelectorAll('[required]');
            let isValid = true;

            requiredInputs.forEach(input => {
                if (!input.value) {
                    input.style.borderColor = 'var(--danger)';
                    isValid = false;

                    // Remove error styling on input
                    input.addEventListener('input', function () {
                        this.style.borderColor = 'var(--light-gray)';
                    });
                }
            });

            if (!isValid) {
                alert('Please fill out all required fields before proceeding.');
            }

            return isValid;
        }
    
 
            // Search Drugs.com for medication recommendations
            function searchDrugsCom() {
                // Show loading spinner
                loadingSpinner.style.display = 'block';
                resultsContainer.style.display = 'none';
                
                // Get form data
                const primarySymptom = document.getElementById('primarySymptom').value;
                const additionalSymptoms = Array.from(document.querySelectorAll('input[name="symptoms"]:checked')).map(el => el.value);
                const duration = document.getElementById('symptomDuration').value;
                const severity = document.getElementById('symptomSeverity').value;
                const age = document.getElementById('age').value;
                const gender = document.getElementById('gender').value;
                const conditions = Array.from(document.querySelectorAll('input[name="conditions"]:checked')).map(el => el.value);
                const currentMeds = document.getElementById('currentMeds').value;
                const allergies = document.getElementById('allergies').value;
                
                // Construct search parameters
                const searchParams = {
                    primarySymptom: primarySymptom,
                    additionalSymptoms: additionalSymptoms,
                    duration: duration,
                    severity: severity,
                    age: age,
                    gender: gender,
                    conditions: conditions,
                    currentMeds: currentMeds,
                    allergies: allergies
                };
                
                console.log("Search parameters:", searchParams);
                
                // Simulate API call with timeout
                setTimeout(() => {
                    // Hide loading spinner
                    loadingSpinner.style.display = 'none';
                    resultsContainer.style.display = 'block';
                    
                    // Display mock results (in a real app, these would come from Drugs.com API)
                    displayMedicationResults(searchParams);
                }, 2000);
            }
            
            // Display medication results
            function displayMedicationResults(params) {
                medicationResults.innerHTML = '';
                
                // Generate mock results based on symptoms
                const medications = getMedicationsForSymptoms(params.primarySymptom, params.additionalSymptoms, params.conditions);
                
                if (medications.length === 0) {
                    const noResults = document.createElement('div');
                    noResults.className = 'medication-card';
                    noResults.innerHTML = `
                        <h3 class="medication-name">No specific medications found</h3>
                        <div class="medication-details">
                            <p>Based on your symptoms and health history, we couldn't find specific medication recommendations.</p>
                            <p>Consider consulting with a healthcare provider for personalized advice.</p>
                        </div>
                    `;
                    medicationResults.appendChild(noResults);
                    return;
                }
                
                // Display each medication
                medications.forEach(med => {
                    const medCard = document.createElement('div');
                    medCard.className = 'medication-card';
                    
                    let warnings = '';
                    if (med.warnings && med.warnings.length > 0) {
                        warnings = `<div class="medication-details warning">Warnings: ${med.warnings.join(' ')}</div>`;
                    }
                    
                    let interactions = '';
                    if (med.interactions && med.interactions.length > 0) {
                        interactions = `
                            <div class="detail-row">
                                <div class="detail-label">Interactions:</div>
                                <div class="detail-value">${med.interactions.join(', ')}</div>
                            </div>
                        `;
                    }
                    
                    medCard.innerHTML = `
                        <div class="medication-header">
                            <h3 class="medication-name">${med.name}</h3>
                            <span class="medication-type">${med.type}</span>
                        </div>
                        <div class="medication-details">
                            <div class="detail-row">
                                <div class="detail-label">Purpose:</div>
                                <div class="detail-value">${med.purpose}</div>
                            </div>
                            <div class="detail-row">
                                <div class="detail-label">Dosage:</div>
                                <div class="detail-value">${med.dosage}</div>
                            </div>
                            <div class="detail-row">
                                <div class="detail-label">Side Effects:</div>
                                <div class="detail-value">${med.sideEffects.join(', ')}</div>
                            </div>
                            ${interactions}
                            <div class="detail-row">
                                <div class="detail-label">More Info:</div>
                                <div class="detail-value"><a href="${med.link}" target="_blank" style="color: var(--primary);">View on Drugs.com</a></div>
                            </div>
                        </div>
                        ${warnings}
                    `;
                    medicationResults.appendChild(medCard);
                });
                
                // Add a note about real implementation
                const noteCard = document.createElement('div');
                noteCard.className = 'medication-card';
                noteCard.innerHTML = `
                    <h3 class="medication-name"><i class="fas fa-info-circle"></i> Note About This Demo</h3>
                    <div class="medication-details">
                        <p>In a real implementation, this section would display actual medication data from Drugs.com's API based on your symptoms and health history. The results above are simulated for demonstration purposes.</p>
                        <p>To implement this with Drugs.com's API, you would need to:</p>
                        <ol>
                            <li>Register for a Drugs.com API key</li>
                            <li>Make API calls to their medication database</li>
                            <li>Filter results based on user's health profile</li>
                            <li>Display the returned medication information</li>
                        </ol>
                        <p>Drugs.com provides comprehensive drug information including side effects, interactions, and dosage guidelines :cite[1].</p>
                    </div>
                `;
                medicationResults.appendChild(noteCard);
            }
            
            // Get medications based on symptoms (mock data)
            function getMedicationsForSymptoms(primarySymptom, additionalSymptoms, conditions) {
                const allMedications = [];
                
                // Base medications on primary symptom
                if (primarySymptom === 'headache') {
                    allMedications.push({
                        name: 'Acetaminophen (Tylenol)',
                        type: 'Over-the-counter',
                        purpose: 'Pain relief and fever reduction',
                        dosage: '500-1000mg every 4-6 hours as needed (max 4000mg/day)',
                        sideEffects: ['Liver damage (if overdosed)', 'Allergic reactions'],
                        warnings: conditions.includes('liver disease') ? ['Not recommended for people with liver disease'] : [],
                        interactions: ['Alcohol', 'Warfarin'],
                        link: 'https://www.drugs.com/acetaminophen.html'
                    });
                    
                    if (!additionalSymptoms.includes('cold') && !conditions.includes('liver disease')) {
                        allMedications.push({
                            name: 'Ibuprofen (Advil, Motrin)',
                            type: 'Over-the-counter',
                            purpose: 'Pain relief, cold reduction, and anti-inflammatory',
                            dosage: '200-400mg every 4-6 hours as needed',
                            sideEffects: ['Stomach upset', 'Increased bleeding risk', 'Kidney problems'],
                            warnings: conditions.includes('kidney disease') ? ['Not recommended for people with kidney disease'] : [],
                            interactions: ['Aspirin', 'Blood pressure medications'],
                            link: 'https://www.drugs.com/ibuprofen.html'
                        });
                    }
                }
                
                if (primarySymptom === 'fever' || additionalSymptoms.includes('cold')) {
                    (primarySymptom === 'fever') 
                        allMedications.push({
                            name: 'Naproxen (Aleve)',
                            type: 'Over-the-counter',
                            purpose: 'Relieves fever, pain, and inflammation',
                            dosage: '220mg every 8-12 hours (max 660mg/day)',
                            sideEffects: ['Stomach upset', 'Dizziness', 'Rash'],
                            warnings: conditions.includes('heart disease') || conditions.includes('stomach ulcer') ? ['Use with caution in heart disease or ulcers'] : [],
                            interactions: ['Aspirin', 'SSRIs', 'Antihypertensives'],
                            link: 'https://www.drugs.com/naproxen.html'
                        });
                    
                    allMedications.push({
                        name: 'Acetaminophen (Tylenol)',
                        type: 'Over-the-counter',
                        purpose: 'Fever reduction and pain relief',
                        dosage: '500-1000mg every 4-6 hours as needed (max 4000mg/day)',
                        sideEffects: ['Liver damage (if overdosed)', 'Allergic reactions'],
                        warnings: conditions.includes('liver disease') ? ['Not recommended for people with liver disease'] : [],
                        interactions: ['Alcohol', 'Warfarin'],
                        link: 'https://www.drugs.com/acetaminophen.html'
                    });
                    
                    if (!conditions.includes('kidney disease')) {
                        allMedications.push({
                            name: 'Ibuprofen (Advil, Motrin)',
                            type: 'Over-the-counter',
                            purpose: 'cold reduction and pain relief',
                            dosage: '200-400mg every 6-8 hours as needed',
                            sideEffects: ['Stomach upset', 'Increased bleeding risk', 'Kidney problems'],
                            warnings: [],
                            interactions: ['Aspirin', 'Blood pressure medications'],
                            link: 'https://www.drugs.com/ibuprofen.html'
                        });
                    }
                }
                
                if (primarySymptom === 'cough') {
                    allMedications.push({
                        name: 'Bromhexine',
                        type: 'Over-the-counter (in some countries)',
                        purpose: 'Mucolytic agent that breaks down mucus and relieves productive cough',
                        dosage: '8-16mg three times a day (adult dose)',
                        sideEffects: ['Stomach upset', 'Nausea', 'Allergic reactions'],
                        warnings: [],
                        interactions: ['Antitussives (may reduce effectiveness)', 'Antibiotics (may enhance absorption)'],
                        link: 'https://www.drugs.com/international/bromhexine.html'
                    });
                    if (additionalSymptoms.includes('nasal congestion')) {
                        allMedications.push({
                            name: 'Dextromethorphan/Guaifenesin (Robitussin DM)',
                            type: 'Over-the-counter',
                            purpose: 'Cough suppression and mucus relief',
                            dosage: '10-20mL every 4 hours as needed',
                            sideEffects: ['Drowsiness', 'Dizziness', 'Nausea'],
                            warnings: [],
                            interactions: ['MAO inhibitors', 'Other cough medicines'],
                            link: 'https://www.drugs.com/robitussin-dm.html'
                        });
                    } else {
                        allMedications.push({
                            name: 'Dextromethorphan (Delsym)',
                            type: 'Over-the-counter',
                            purpose: 'Cough suppression',
                            dosage: '10-20mg every 4 hours as needed',
                            sideEffects: ['Drowsiness', 'Dizziness'],
                            warnings: [],
                            interactions: ['MAO inhibitors', 'Other cough medicines'],
                            link: 'https://www.drugs.com/dextromethorphan.html'
                        });
                    }
                }
                
                if (primarySymptom === 'sore throat') {
                    allMedications.push({
                        name: 'Benzocaine (Chloraseptic)',
                        type: 'Over-the-counter',
                        purpose: 'Sore throat pain relief',
                        dosage: 'Spray or lozenge as directed every 2 hours',
                        sideEffects: ['Mild stinging', 'Numbness'],
                        warnings: ['Do not use for more than 2 days without consulting doctor'],
                        interactions: [],
                        link: 'https://www.drugs.com/chloraseptic.html'
                    });
                }
                
                if (primarySymptom === 'heartburn') {
                    allMedications.push({
                        name: 'Omeprazole (Prilosec)',
                        type: 'Over-the-counter',
                        purpose: 'Reduces stomach acid to relieve heartburn, acid reflux, and GERD',
                        dosage: '20mg once daily before a meal (usually taken for 14 days)',
                        sideEffects: ['Headache', 'Stomach pain', 'Gas', 'Nausea'],
                        warnings: conditions.includes('liver disease') ? ['Use with caution in liver impairment'] : [],
                        interactions: ['Clopidogrel', 'Warfarin', 'Methotrexate', 'Diazepam'],
                        link: 'https://www.drugs.com/omeprazole.html'
                    });

                    allMedications.push({
                        name: 'Famotidine (Pepcid)',
                        type: 'Over-the-counter',
                        purpose: 'Heartburn relief',
                        dosage: '10-20mg every 12 hours as needed',
                        sideEffects: ['Headache', 'Constipation', 'Diarrhea'],
                        warnings: [],
                        interactions: ['Atazanavir', 'Dasatinib'],
                        link: 'https://www.drugs.com/famotidine.html'
                    });
                    
                    if (!conditions.includes('kidney disease')) {
                        allMedications.push({
                            name: 'Furosemide (Lasix)',
                            type: 'Prescription-only',
                            purpose: 'Reduces fluid overload (edema) in people with kidney disease or heart failure',
                            dosage: '20-80mg once or twice daily (adjusted based on response)',
                            sideEffects: ['Dehydration', 'Low potassium', 'Dizziness'],
                            warnings: ['Monitor electrolytes and kidney function regularly'],
                            interactions: ['NSAIDs', 'Aminoglycosides', 'Lithium'],
                            link: 'https://www.drugs.com/furosemide.html'
                        });

                        allMedications.push({
                            name: 'Omeprazole (Prilosec OTC)',
                            type: 'Over-the-counter',
                            purpose: 'Frequent heartburn relief',
                            dosage: '20mg once daily for 14 days',
                            sideEffects: ['Headache', 'Abdominal pain', 'Diarrhea'],
                            warnings: ['Do not use for more than 14 days without consulting doctor'],
                            interactions: ['Clopidogrel', 'Methotrexate'],
                            link: 'https://www.drugs.com/omeprazole.html'
                        });
                    }
                }
                
                if (primarySymptom === 'diarrhea') {
                    allMedications.push({
                        name: 'Bismuth Subsalicylate (Pepto-Bismol)',
                        type: 'Over-the-counter',
                        purpose: 'Reduces diarrhea, nausea, and stomach discomfort',
                        dosage: '524mg every 30-60 minutes as needed (max 8 doses/day)',
                        sideEffects: ['Black tongue or stools', 'Constipation', 'Tinnitus (ringing in ears)'],
                        warnings: conditions.includes('aspirin allergy') || conditions.includes('bleeding disorder') ? 
                            ['Avoid if allergic to aspirin or with bleeding risk'] : [],
                        interactions: ['Anticoagulants', 'Tetracycline antibiotics'],
                        link: 'https://www.drugs.com/bismuth-subsalicylate.html'
                    });

                    allMedications.push({
                        name: 'Loperamide (Imodium)',
                        type: 'Over-the-counter',
                        purpose: 'Diarrhea relief',
                        dosage: '2mg after first loose stool, then 1mg after each subsequent stool (max 8mg/24hr)',
                        sideEffects: ['Constipation', 'Dizziness', 'Drowsiness'],
                        warnings: ['Do not use if you have fever or bloody stools'],
                        interactions: ['Quinidine', 'Ritonavir'],
                        link: 'https://www.drugs.com/loperamide.html'
                    });
                }
                
                if (primarySymptom === 'constipation') {
                    allMedications.push({
                        name: 'Polyethylene Glycol (Miralax)',
                        type: 'Over-the-counter',
                        purpose: 'Constipation relief',
                        dosage: '17g powder in 4-8oz liquid daily',
                        sideEffects: ['Bloating', 'Gas', 'Nausea'],
                        warnings: conditions.includes('pregnant') ? ['Consult doctor before use if pregnant'] : [],
                        interactions: [],
                        link: 'https://www.drugs.com/miralax.html'
                    });
                }
                
                if (primarySymptom === 'rash') {
                    allMedications.push({
                        name: 'Hydrocortisone Cream 1%',
                        type: 'Over-the-counter',
                        purpose: 'Itch and rash relief',
                        dosage: 'Apply thin layer to affected area 1-2 times daily',
                        sideEffects: ['Skin thinning (with prolonged use)', 'Burning sensation'],
                        warnings: ['Do not use on face or genitals unless directed by doctor'],
                        interactions: [],
                        link: 'https://www.drugs.com/hydrocortisone-topical.html'
                    });
                }
                
                // Filter medications based on conditions and allergies
                return allMedications.filter(med => {
                    // In a real implementation, you would check against actual conditions and allergies
                    return true;
                });
            }
            
            // In a real implementation, you would have a function like this to call Drugs.com API:
            /*
            async function callDrugsComAPI(params) {
                const apiKey = 'YOUR_DRUGS_COM_API_KEY';
                const url = `https://api.drugs.com/v1/medications?primarySymptom=${encodeURIComponent(params.primarySymptom)}&conditions=${encodeURIComponent(params.conditions.join(','))}`;
                
                try {
                    const response = await fetch(url, {
                        headers: {
                            'Authorization': `Bearer ${apiKey}`
                        }
                    });
                    const data = await response.json();
                    return data.medications || [];
                } catch (error) {
                    console.error('Error calling Drugs.com API:', error);
                    return [];
                }
            }
            */
        });
    </script>
</body>
</html>
