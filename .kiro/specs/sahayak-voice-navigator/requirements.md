# Requirements Document

## Introduction

Sahayak is an AI-powered voice-first government scheme navigator designed for rural India. The system helps underserved citizens discover and understand government welfare schemes they are eligible for through natural voice conversations in local languages. The system addresses the critical problem that 40-60% of eligible beneficiaries never claim their entitlements due to information asymmetry, literacy barriers, and digital divide.

The system enables users to speak naturally about their life situation, extracts a structured profile from the conversation, cross-references against 700+ government schemes, and returns personalized eligibility results with actionable guidance—all through voice interaction in the user's preferred language.

## Glossary

- **System**: The Sahayak voice-first government scheme navigator application
- **User**: A citizen seeking information about government welfare schemes
- **Profile**: Structured data extracted from user conversation including demographics, economic status, and social category
- **Scheme**: A government welfare program with defined eligibility criteria and benefits
- **Scheme_Database**: The curated knowledge base of 700+ central and state government schemes
- **Voice_Input_Module**: Component that captures and transcribes user speech
- **Voice_Output_Module**: Component that generates and plays audio responses
- **AI_Engine**: Google Gemini API service for natural language understanding and reasoning
- **Eligibility_Matcher**: Component that matches user profiles against scheme criteria
- **Session**: A single conversation instance between user and system
- **Offline_Mode**: System operation without active internet connectivity
- **PWA**: Progressive Web Application - installable web application
- **STT**: Speech-to-Text conversion service
- **TTS**: Text-to-Speech conversion service
- **Confidence_Score**: Numerical indicator of eligibility match certainty
- **Document_Checklist**: Consolidated list of required documents for scheme applications
- **Scheme_Card**: Structured presentation of scheme details including benefits and application process

## Requirements

### Requirement 1: Voice Input Capture and Transcription

**User Story:** As a rural user with limited literacy, I want to speak naturally about my situation in my local language, so that I can interact with the system without reading or typing.

#### Acceptance Criteria

1. WHEN a user initiates a voice session, THE Voice_Input_Module SHALL activate the microphone and begin capturing audio
2. WHEN audio is captured through the browser, THE Voice_Input_Module SHALL use Web Speech API for on-device speech-to-text conversion
3. IF Web Speech API fails or is unavailable, THEN THE Voice_Input_Module SHALL send the audio to Amazon Transcribe for server-side transcription
4. WHEN transcribing Hindi speech, THE Voice_Input_Module SHALL support major dialect variations from UP, Bihar, MP, Rajasthan, and Haryana
5. WHEN transcription is complete, THE System SHALL return the text within 2 seconds for on-device processing or within 5 seconds for server-side processing
6. THE Voice_Input_Module SHALL support Hindi and English languages in the MVP version
7. WHEN background noise is detected, THE Voice_Input_Module SHALL apply noise filtering before transcription
8. WHEN transcription confidence is below 60%, THE System SHALL prompt the user to repeat their input

### Requirement 2: Profile Extraction from Natural Language

**User Story:** As a user, I want the system to understand my life situation from natural conversation, so that I don't have to fill complex forms or understand technical eligibility criteria.

#### Acceptance Criteria

1. WHEN transcribed text is received, THE AI_Engine SHALL extract structured profile attributes including age, gender, location, social category, income, occupation, family composition, education, health status, and housing situation
2. WHEN extracting social category, THE AI_Engine SHALL map colloquial terms to standard categories (SC, ST, OBC, General, Minority)
3. WHEN extracting income information, THE AI_Engine SHALL normalize various income expressions to annual income in rupees
4. WHEN extracting location, THE AI_Engine SHALL identify state, district, and rural/urban classification
5. WHEN critical profile attributes are missing, THE AI_Engine SHALL identify which attributes are needed for scheme matching
6. THE AI_Engine SHALL achieve at least 85% accuracy in profile attribute extraction compared to manual annotation
7. WHEN ambiguous information is provided, THE AI_Engine SHALL request clarification through follow-up questions
8. THE AI_Engine SHALL extract profile data within 3 seconds of receiving transcribed text

### Requirement 3: Scheme Eligibility Matching

**User Story:** As a user, I want to discover all government schemes I'm eligible for based on my profile, so that I don't miss any entitlements I qualify for.

#### Acceptance Criteria

1. WHEN a complete user profile is extracted, THE Eligibility_Matcher SHALL query the Scheme_Database for matching schemes
2. WHEN matching schemes, THE Eligibility_Matcher SHALL evaluate multi-dimensional criteria including age range, income ceiling, social category, occupation, location, gender, family size, and education level
3. WHEN a scheme matches the user profile, THE Eligibility_Matcher SHALL calculate a Confidence_Score from 1 to 5 stars
4. THE Eligibility_Matcher SHALL achieve at least 90% precision in eligibility determination
5. THE Eligibility_Matcher SHALL achieve at least 75% recall in finding eligible schemes
6. WHEN multiple schemes match, THE Eligibility_Matcher SHALL rank schemes by monetary value, ease of application, and deadline urgency
7. THE Eligibility_Matcher SHALL complete matching against 700+ schemes within 2 seconds
8. WHEN eligibility is uncertain, THE Eligibility_Matcher SHALL include the scheme with a lower Confidence_Score and explanatory note

### Requirement 4: Voice Response Generation

**User Story:** As a user with limited literacy, I want to hear scheme information in my language through natural voice, so that I can understand my options without reading text.

#### Acceptance Criteria

1. WHEN eligible schemes are identified, THE Voice_Output_Module SHALL generate audio responses in the user's selected language
2. WHEN generating Hindi audio, THE Voice_Output_Module SHALL use Amazon Polly neural voice "Kajal" for natural-sounding speech
3. WHEN internet connectivity is available, THE Voice_Output_Module SHALL use Amazon Polly for high-quality voice synthesis
4. WHEN operating offline, THE Voice_Output_Module SHALL use Web Speech API as fallback for voice synthesis
5. WHEN presenting scheme information, THE Voice_Output_Module SHALL speak the scheme name, benefits, required documents, and application process
6. THE Voice_Output_Module SHALL limit voice summaries to the top 5 eligible schemes to maintain user attention
7. WHEN voice output is playing, THE System SHALL provide visual controls to pause, replay, or skip
8. THE Voice_Output_Module SHALL generate and begin playing audio within 3 seconds of receiving scheme data

### Requirement 5: Scheme Information Presentation

**User Story:** As a user, I want to see and hear detailed information about each scheme I'm eligible for, so that I can understand the benefits and know how to apply.

#### Acceptance Criteria

1. WHEN displaying scheme information, THE System SHALL present a Scheme_Card containing scheme name, department, eligibility reason, benefits, required documents, application process, deadline, and Confidence_Score
2. WHEN showing required documents, THE System SHALL indicate which documents the user already has based on their profile
3. WHEN showing required documents, THE System SHALL indicate which documents need to be obtained and where to get them
4. WHEN presenting application process, THE System SHALL provide both online and offline application options if available
5. WHEN showing office locations, THE System SHALL identify the nearest relevant government office based on user location
6. THE System SHALL display monetary benefits in rupees with clear explanation of payment frequency
7. WHEN a scheme has application deadlines, THE System SHALL prominently display the deadline date
8. THE System SHALL present schemes in priority order with highest-value or most urgent schemes first

### Requirement 6: Document Guidance and Checklist

**User Story:** As a user preparing to apply for schemes, I want a consolidated list of all documents I need, so that I can gather everything in one trip and avoid wasted visits to government offices.

#### Acceptance Criteria

1. WHEN multiple schemes are identified, THE System SHALL generate a consolidated Document_Checklist containing all unique documents needed across all schemes
2. WHEN presenting the Document_Checklist, THE System SHALL indicate which documents the user already has
3. WHEN presenting the Document_Checklist, THE System SHALL provide guidance on how to obtain each missing document
4. WHEN presenting the Document_Checklist, THE System SHALL identify which government office issues each document
5. THE System SHALL group documents by issuing authority to optimize user trips
6. WHEN a document is required by multiple schemes, THE System SHALL indicate which schemes need that document
7. THE System SHALL provide voice explanation of the Document_Checklist in addition to visual display
8. THE System SHALL allow users to generate a shareable PDF or image of the Document_Checklist

### Requirement 7: Offline Capability

**User Story:** As a rural user with intermittent connectivity, I want the system to work without internet after initial setup, so that I can access scheme information even in areas with poor network coverage.

#### Acceptance Criteria

1. WHEN the PWA is first loaded, THE System SHALL download and cache the complete Scheme_Database to local storage
2. WHEN operating offline, THE System SHALL perform scheme matching using the locally cached Scheme_Database
3. WHEN operating offline, THE System SHALL use Web Speech API for voice input and output
4. WHEN internet connectivity is unavailable, THE System SHALL display an indicator showing offline mode is active
5. THE System SHALL store the Scheme_Database in IndexedDB for persistent offline access
6. WHEN the Scheme_Database is updated on the server, THE System SHALL sync the latest data when connectivity is restored
7. THE System SHALL function fully offline for scheme lookup, document guidance, and information display
8. WHEN AI-powered profile extraction is needed offline, THE System SHALL fall back to guided question-and-answer mode

### Requirement 8: Low Bandwidth Optimization

**User Story:** As a user in an area with 2G connectivity, I want the system to work on slow connections, so that I can access scheme information despite poor network quality.

#### Acceptance Criteria

1. THE System SHALL function on connections as slow as 50-100 kbps (2G speeds)
2. WHEN loading the application, THE System SHALL serve a minimal initial payload of less than 500KB
3. WHEN transmitting audio, THE System SHALL compress audio data to minimize bandwidth usage
4. WHEN loading scheme data, THE System SHALL use compressed JSON bundles served from CloudFront CDN
5. THE System SHALL lazy-load non-critical resources after initial page render
6. WHEN network latency is high, THE System SHALL show progressive loading indicators
7. THE System SHALL cache all static assets using service workers for subsequent visits
8. WHEN API requests timeout due to poor connectivity, THE System SHALL retry with exponential backoff up to 3 attempts

### Requirement 9: Privacy and Data Protection

**User Story:** As a user sharing sensitive personal information, I want my data to be protected and not stored permanently, so that my privacy is maintained.

#### Acceptance Criteria

1. THE System SHALL process all user conversations without storing personal data on servers after the session ends
2. WHEN a session is created, THE System SHALL store conversation state in Redis cache with automatic expiration after 30 minutes
3. WHEN audio is recorded, THE System SHALL process it in real-time and SHALL NOT store audio files on servers
4. WHEN displaying sensitive information like caste or income, THE System SHALL show it only in voice output and not persist it on screen
5. THE System SHALL not require user authentication or account creation
6. WHEN a user closes the session, THE System SHALL immediately clear all session data from cache
7. THE System SHALL communicate privacy policy through voice at session start
8. THE System SHALL allow users to skip sensitive questions without blocking access to scheme information

### Requirement 10: Multi-Device Compatibility

**User Story:** As a user with a basic Android smartphone, I want the system to work smoothly on my device, so that I can access scheme information without needing expensive hardware.

#### Acceptance Criteria

1. THE System SHALL run on Android devices version 8.0 and above
2. THE System SHALL function on devices with minimum 2GB RAM
3. THE System SHALL be installable as a PWA without requiring app store download
4. WHEN installed as PWA, THE System SHALL provide an app icon on the device home screen
5. THE System SHALL be responsive and functional on screen sizes from 4 inches to 7 inches
6. THE System SHALL work on devices with limited storage by keeping total app size under 50MB including cached data
7. THE System SHALL support both portrait and landscape orientations
8. THE System SHALL function on devices running Chrome, Firefox, or Samsung Internet browsers

### Requirement 11: Scheme Database Management

**User Story:** As a system administrator, I want the scheme database to be accurate and up-to-date, so that users receive correct eligibility information.

#### Acceptance Criteria

1. THE Scheme_Database SHALL contain structured data for at least 100 major central and state government schemes in the MVP
2. WHEN storing scheme data, THE System SHALL include scheme name, department, level (central/state), eligibility criteria, benefits, required documents, application process, and deadlines
3. WHEN storing eligibility criteria, THE System SHALL encode them as structured JSON rules for programmatic matching
4. THE Scheme_Database SHALL be stored in DynamoDB with single-digit millisecond query latency
5. WHEN scheme data is updated, THE System SHALL generate a new offline bundle and push it to S3 and CloudFront
6. THE System SHALL display a "last updated" timestamp with scheme information
7. WHEN scheme data is missing or incomplete, THE System SHALL log the gap for manual review
8. THE Scheme_Database SHALL support querying by multiple attributes including category, location, occupation, and age range

### Requirement 12: Error Handling and Fallbacks

**User Story:** As a user encountering technical issues, I want the system to handle errors gracefully and provide alternatives, so that I can still access scheme information.

#### Acceptance Criteria

1. WHEN the AI_Engine API fails, THE System SHALL fall back to guided question-and-answer mode for profile collection
2. WHEN voice input fails, THE System SHALL provide a text input option as fallback
3. WHEN voice output fails, THE System SHALL display text on screen as fallback
4. WHEN the Scheme_Database query fails, THE System SHALL retry up to 3 times before showing an error message
5. WHEN network connectivity is lost mid-session, THE System SHALL switch to offline mode and continue with cached data
6. WHEN an error occurs, THE System SHALL log the error to CloudWatch for monitoring
7. WHEN displaying error messages, THE System SHALL provide clear guidance on what the user should do next
8. THE System SHALL maintain conversation state during transient errors to avoid forcing users to restart

### Requirement 13: Performance and Scalability

**User Story:** As a user, I want the system to respond quickly to my queries, so that I can get scheme information without long waits.

#### Acceptance Criteria

1. THE System SHALL return complete voice responses within 5 seconds on 4G connections
2. THE System SHALL return complete voice responses within 8 seconds on 3G connections
3. WHEN processing profile extraction, THE AI_Engine SHALL respond within 3 seconds
4. WHEN matching schemes, THE Eligibility_Matcher SHALL complete processing within 2 seconds
5. THE System SHALL handle at least 100 concurrent users without performance degradation
6. WHEN API Gateway receives requests, THE System SHALL apply rate limiting to prevent abuse
7. THE System SHALL use AWS Lambda auto-scaling to handle traffic spikes
8. THE System SHALL cache frequently accessed scheme data in CloudFront edge locations

### Requirement 14: Conversation Flow Management

**User Story:** As a user having a conversation with the system, I want the interaction to feel natural and allow me to provide information in any order, so that I don't feel constrained by rigid forms.

#### Acceptance Criteria

1. WHEN a user starts a session, THE System SHALL greet the user and explain how to interact in their selected language
2. WHEN a user provides information, THE System SHALL acknowledge receipt and indicate what information is still needed
3. WHEN sufficient information is collected, THE System SHALL proceed to scheme matching without requiring explicit confirmation
4. WHEN a user provides additional information mid-conversation, THE System SHALL update the profile and re-run eligibility matching
5. THE System SHALL allow users to ask clarifying questions about schemes at any point
6. WHEN a user asks about a specific scheme, THE System SHALL provide detailed information even if not in the eligible list
7. THE System SHALL maintain conversation context across multiple exchanges within a session
8. WHEN a conversation is idle for more than 5 minutes, THE System SHALL prompt the user to continue or end the session

### Requirement 15: Accessibility and Inclusivity

**User Story:** As a user with disabilities or special needs, I want the system to be accessible to me, so that I can access scheme information independently.

#### Acceptance Criteria

1. THE System SHALL support voice-only interaction without requiring any visual input
2. WHEN displaying visual information, THE System SHALL use high-contrast colors and large fonts for readability
3. THE System SHALL support screen reader compatibility for visually impaired users
4. WHEN presenting audio, THE System SHALL provide adjustable playback speed controls
5. THE System SHALL support both male and female voice options for TTS output
6. WHEN a user has hearing impairment, THE System SHALL provide full text transcripts of all audio
7. THE System SHALL avoid flashing or rapidly changing visual elements that could trigger seizures
8. THE System SHALL provide alternative input methods including text and touch for users who cannot use voice

### Requirement 16: Scheme Discovery and Exploration

**User Story:** As a user curious about available schemes, I want to explore different categories of schemes, so that I can learn about programs I might not have known to ask about.

#### Acceptance Criteria

1. THE System SHALL provide a browse mode to explore schemes by category (agriculture, education, healthcare, housing, pensions, skill development)
2. WHEN browsing schemes, THE System SHALL display scheme cards with basic information
3. WHEN a user selects a scheme, THE System SHALL provide full details including eligibility criteria
4. THE System SHALL allow users to search for schemes by keyword or scheme name
5. WHEN displaying scheme categories, THE System SHALL show the count of schemes in each category
6. THE System SHALL highlight schemes with upcoming deadlines in browse mode
7. THE System SHALL allow users to filter schemes by benefit type (monetary, subsidy, service)
8. WHEN a user explores a scheme they're not eligible for, THE System SHALL explain which criteria they don't meet

### Requirement 17: Result Sharing and Export

**User Story:** As a user who needs to show scheme information to family or government officials, I want to save and share my results, so that I can reference them later or get help with applications.

#### Acceptance Criteria

1. WHEN scheme results are displayed, THE System SHALL provide an option to generate a shareable report
2. WHEN generating a report, THE System SHALL create a PDF or image containing all eligible schemes and the Document_Checklist
3. THE System SHALL allow users to share the report via WhatsApp, SMS, or email
4. WHEN generating shareable content, THE System SHALL exclude sensitive personal information like caste and income details
5. THE System SHALL provide a unique session ID that users can reference when seeking help
6. THE System SHALL allow users to download the report to their device storage
7. WHEN sharing results, THE System SHALL include a disclaimer that final eligibility is determined by government offices
8. THE System SHALL generate shareable reports in the user's selected language

### Requirement 18: Monitoring and Analytics

**User Story:** As a system administrator, I want to monitor system performance and usage patterns, so that I can identify issues and improve the service.

#### Acceptance Criteria

1. THE System SHALL log all API requests to CloudWatch with timestamp, endpoint, latency, and status code
2. WHEN errors occur, THE System SHALL log error details including stack traces to CloudWatch
3. THE System SHALL track conversation completion rates (percentage of users who complete the full flow)
4. THE System SHALL track average session duration and number of exchanges per session
5. THE System SHALL monitor AI_Engine response times and accuracy metrics
6. THE System SHALL track which schemes are most frequently matched
7. THE System SHALL use AWS X-Ray for distributed tracing across Lambda, API Gateway, and external services
8. THE System SHALL set up CloudWatch alarms for error rates exceeding 5% and latency exceeding 10 seconds

### Requirement 19: Security and Abuse Prevention

**User Story:** As a system operator, I want to protect the system from abuse and attacks, so that legitimate users can access the service reliably.

#### Acceptance Criteria

1. THE System SHALL use AWS WAF to protect API Gateway from common web attacks
2. WHEN API requests exceed 100 per minute from a single IP, THE System SHALL apply rate limiting
3. THE System SHALL validate all input data to prevent injection attacks
4. THE System SHALL use HTTPS for all client-server communication
5. THE System SHALL store API keys and credentials in AWS Secrets Manager
6. THE System SHALL use IAM roles with least-privilege permissions for all Lambda functions
7. WHEN suspicious activity is detected, THE System SHALL log the incident and temporarily block the source
8. THE System SHALL implement CORS policies to restrict API access to authorized domains

### Requirement 20: Deployment and DevOps

**User Story:** As a developer, I want automated deployment and infrastructure management, so that I can deploy updates quickly and reliably.

#### Acceptance Criteria

1. THE System SHALL use Infrastructure-as-Code (AWS SAM or SST) for all AWS resource provisioning
2. WHEN code is pushed to the main branch, THE System SHALL automatically trigger a build and deployment pipeline
3. THE System SHALL deploy the Astro frontend to S3 and invalidate CloudFront cache on each deployment
4. THE System SHALL run automated tests before deploying to production
5. THE System SHALL maintain separate environments for development, staging, and production
6. WHEN deployment fails, THE System SHALL automatically roll back to the previous stable version
7. THE System SHALL use GitHub Actions or AWS CodePipeline for CI/CD automation
8. THE System SHALL provide deployment status notifications via email or Slack
