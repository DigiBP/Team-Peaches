#AS IS Situation
The AS IS process is described and modelled as a strategic process model according to Freund & Rücker (Freund & Rücker, 2019). This enables the involved stakeholders a basic understanding of the current situation on a high level.

##Stakeholders
![image](https://user-images.githubusercontent.com/105595416/233787342-aede7296-d0a5-4e14-a651-af36274caedd.png)

##Process: Compile Candidate Shortlist
The starting point for the process in scope is a job advertisement that is ready for publishing and ends with the first shortlist of candidates who all fulfill the must-criteria.
An HR manager has a finalized job advertisement for an open position and posts this on one or several online job platforms. All interested people are reading it, potential candidates prepare and submit their application dossier according to the available information from the job advertisement. 
The HR manager receives all submitted dossiers and creates a file for each candidate, before confirming the entrance of the application to each candidate. After a certain time, the responsible HR manager checks the dossiers of all applications received and categorizes the dossiers in three different groups. The responsible line manager does the same afterwards. After working on the dossiers, the HR manager invites all shortlist candidates (high potentials) for a first interview. In case enough first interviews are confirmed, the HR manager rejects all application of non-suitable candidates and deactivates the job advertisement. When not enough first round interviews are confirmed, the job advertisement is reposted by the HR manager again, maybe on other job portals additionally.

##Pains
Because not all relevant information were transparent before the candidates prepared and submitted their dossier, the HR and line manager spent time on dossiers they wouldn’t have received otherwise. In addition, the candidates who submitted their dossiers without fulfilling the must-criteria’s or without knowing the relevant salary range spent time and effort for the waste as well. Their motivation and attitude towards the company decreases quite fast, if they later in the process realize that their application was for the waste already at the beginning. These circumstances reduce efficiency and damages the reputation of a company and its employer branding as well.


#TO BE Situation
In order to keep the process lean and to reach a stable process flow, the project team decided to split the former AS IS process into three single processes. This approach ensures that the single processes can be used as a trigger for other ones and that each application can be processed as an instance.

##Stakeholders
![image](https://user-images.githubusercontent.com/105595416/233787609-3d81aa46-c337-4746-bc2b-de798b4ddf3a.png)

##Process: Job Advertisement to Candidate Notification
An HR manager has a finalized job advertisement for an open position. He or she captures needed meta data like wage grade, job title and text, office location and duration of job ad in a Camunda form. The system creates a specific business key for that open position and a related data folder on Google drive. In addition, the system generates a specific application form for that open position, stores that form on Google drive and inserts the new open position also in the overall job information spreadsheet on Google. Finally, the HR manager posts the job advertisement on one or several online job platforms with a direct link to the wage grade request form. 
As soon the duration of the job advertisement is expired, the HR manager receives a task in Camunda to deactivate the job ad and specific forms that were created only for this position. Depending on the number of received application dossiers, the non-interrupting sub-process for the intermediate Application Reviews took place one or several times since the job ad was published. 
The HR manager reviews and ranks all received dossiers before the responsible line manager is doing the same. As soon all dossiers are reviewed and ranked, the HR manager invites desirable candidates for a first interview and sends a rejection to non-suitable candidates. In parallel, the system extracts statistical data regarding the published job ad, anonymizes this data and stores it to Google drive.


##Process: Salary Request to Application Storage
Potential candidates can check their “candidate-position-fit” with the possible salary range for the open position. The process starts with a digital form that is completed by the candidate. This form collects information like age, education, experience, main skills and if the candidate has children below 16 years or not. All information is collected in a structured way by pre-defined cells. 
The process checks if the diploma criteria are fulfilled; if not, the candidate receives the appropriate information, and the process is already finished.
If the diploma criteria are fulfilled, the process checks in parallel the maximum salary, the corresponding deduction factor, and the possible child/ educational allowances the potential candidate would get. All these factors are needed to calculate the approximate salary and the maximum salary a specific potential candidate would get. The system informs the candidate in a message and provides him or her directly with a corresponding link for a dossier submission. 
With this feedback, the potential candidate is either fully motivated to prepare and apply for the position, or the potential candidate is not more interested in the open position and doesn’t invest time for an application process without positive outcomes.
If a potential candidate decides to apply officially for the position, the whole application dossier has to be prepared and submitted. After receiving this dossier, the system sends a confirmation to the official candidate, saves the candidate dossier accordingly in a new drive folder.
If the potential candidate does not respond or submit a dossier after receiving the calculation outcome, the process gets finished after 10 days automatically.


##Process: Intermediate Application Review
Each submitted dossier creates a new row in a google sheet. The MAKE Scenario observes and counts all submissions; every time the mark of 10 unreviewed dossier is reached, it triggers a message flow to the process “Job Advertisement to Candidate Notification” and starts the non-interrupting sub-process “Intermediate Application Review”.

##Gains
Thanks to the digitalized processes, the first shortlist includes already only candidates who are aware of their “candidates-position-fit” and the applicable salary range. Both the candidates and the hiring company do not waste time and effort for unmatching applications.
