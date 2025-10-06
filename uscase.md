| Use Case | Description | Notes |
| --- | --- | --- |
| Minutes of Meeting to To-do to Calendar |  | Extraction of specific parts of Minutes of Meetings (to-do, deadlines) can be done by specifiying specific way of writing in the minutes and by making developing specific prompts for the LLM. |
| Document Analysis. Corrected OCR + Document Summary. Chatbot Query |  | All tools for this are readily available. |
| Sales Team WA Analysis |  | All tools for this are readily available. |

# Use Case 1: Minutes of Meeting to To-do to Calendar

## **Objective**

To improve workflows by adding a feature that processes meeting minutes (digital documents) to extract summaries as to-do lists with deadlines and integrates these tasks into a departmental calendar for efficient task management and tracking.

## **Use Case Overview**

| **Section** | **Details** |  |
| --- | --- | --- |
| **Context** | Meeting minutes (documents) are uploaded to the system, processed to identify action items and deadlines, and converted into to-do lists. These tasks are then automatically or manually integrated into a departmental calendar, ensuring team alignment and timely completion.<br><br>Meeting minutes (documents) are accessed from a local folder, processed to identify action items and deadlines, and converted into structured to-do lists. To ensure accurate extraction, sentences may need to follow a defined syntax or structure so the system can reliably recognize which lines should be converted into tasks. These tasks are then automatically or manually integrated into a departmental calendar, ensuring team alignment and timely completion. | There maybe a certain sentence structure/syntax that must be followed for the system to identify which line has to be converted into task list. |
| **Access Channels** | Using PKC for uploads, task review, and calendar integration. |  |
| **User Flow** | Users log in, upload meeting minutes, review extracted to-do lists and deadlines, approve or edit tasks, and integrate them into a departmental calendar. Notifications confirm task assignments and calendar updates. |  |
| **Confirmation** | Successful processing generates an in-app or email notification with a link to view the to-do list and calendar entries. Calendar updates are reflected in real-time for authorized users. |  |

## **Functional Requirements**

| **Section** | **Details** | Comments |
| --- | --- | --- |
| **1. Document Access for Meeting Minutes** | - **Supported Formats:** PDF or docs meeting minutes.<br>- Source: Users select a local folder, and the system automatically detects available files (no manual upload).<br>- Supported Formats: PDF, DOC/DOCX.<br>- Processing: Content extraction and summarization handled by the LLM. | Supported when users self-host PKC on their own machine. Recommended setup: grant PKC read access to a designated folder and enable a background watcher to detect new/updated files. Nothing leaves the device unless the user chooses to share/export. |
| **2. To-Do List Extraction** | - **Action Item Identification:** AI analyzes text to identify action items (e.g., “Prepare report by Jimmy” or “Follow up with resident”).<br>- **Deadline Extraction:** Detects deadlines (e.g., “by Friday” or “by 15-Sep-2025”) and associates them with tasks.<br>- **Output Format:** To-do list in a structured format (e.g., table with columns: Task, Assignee, Deadline, Status).<br>- **Editable:** Users can modify tasks, assignees, or deadlines before finalizing. | Feasible with high accuracy. Best practice: adopt a simple sentence pattern in minutes (e.g., "[Owner] to [Action] by [Date]") and ship a prompt library for extraction. Provide a review UI (human-in-the-loop) before saving tasks to avoid misclassification. |
| **3. Departmental Calendar Integration** | - **Calendar Compatibility:** Integrates with common calendar systems (e.g., Google Calendar or Microsoft Outlook).<br>- **Task Assignment:** Tasks are assigned to individuals or departments and added as calendar events with deadlines.<br>- **Access Control:** Only authorized users (e.g., department heads) can view/edit calendar entries. | Primary path: Google Calendar. Users connect their Google account from PKC and import tasks as events; scopes limited to calendar access only. Fallback: export ICS for manual import if OAuth is not available. |
| **4. Customizable Task Categories** | - Authorized user define task categories (e.g., “Urgent,” “Follow-Up,” “Project”) for organizing to-do lists.<br>- Categories editable anytime to reflect department needs. | Possible but not in current plan. Suggested roadmap: start with free-form tags as MVP, then add an admin-managed taxonomy with color-coding and visibility rules in a later phase. |
| **5. Notifications and Reminders** | - **Processing Confirmation:** Email notification with link to to-do list and summary after processing.<br>- **Task Reminders:** User-defined reminders for tasks (e.g., 3 days, 1 day before deadline).<br>- **Calendar Updates:** Notifies team when tasks are added to the calendar.<br>- **Error Alerts:** Notifies user if processing fails (e.g., unclear text) with re-upload suggestion. | Phase 1: WhatsApp/Telegram via bot + email (SMTP) with configurable reminder cadence. Future: in-app push and digest summaries. Delivery failures are surfaced with retry guidance. |
| **6. Searchable Task and Document Archive** | - **Search:** Keyword search across meeting minutes, to-do lists, and calendar events (e.g., “tasks assigned to Jimmy”).<br>- **Filters:** By department, date, category, or status (e.g., “Pending”).<br>- **Indexing:** Fast search via database.<br>- **Version Control:** Tracks updates to minutes or tasks. | Supported. Locally indexed for privacy; include both keyword and semantic search for tasks and minutes metadata. Versioning is content-hash based so changes are tracked and reversible. |
| **7. Chatbot Query for Tasks** | - **Queries:** Users ask questions about tasks or minutes (e.g., “What tasks are due this week?” or “Who is assigned to the budget report?”).<br>- **Context:** Chatbot uses minutes and to-do lists for accurate answers.<br>- **Follow-Ups:** Supports multi-turn conversations.<br>- **Error Handling:** Requests clarification for unclear questions. | Achievable with grounded answers: the bot cites the source lines from minutes and the task IDs. Includes disambiguation prompts when multiple matches exist and avoids hallucination by restricting to indexed content. |
| **8. Export Capabilities** | - **Formats:** Export to-do lists, summaries, or calendar events as PDF, docs or ICS (calendar format).<br>- **Process:** One-click download from task or document page.<br>- **Batch Export:** Option to export tasks from multiple meetings. | Users can export/convert or create files. Include CSV/Excel export for tasks, ICS for calendar, and redaction options for sensitive fields before sharing. |
| **9. Multi-Language Support** | - **Enable/Disable:** Admins toggle multi-language OCR and task extraction.<br>- **Languages:** Supports common company languages (e.g., English, Indonesian).<br>- **Validation:** Auto-detects document language for processing.<br>- Covered by LLM: The system can automatically detect and process multiple languages without additional configuration. | Possible. OCR/LLM pipelines auto-detect language; date/time parsing is locale-aware to avoid deadline misinterpretation. |
| **10. Group/Departmental Task Management** | - **Permissions:** Authorized user assign task visibility to departments (e.g., Finance sees only their tasks).<br>- **Shared Access:** Teams share tasks via codes/links. | Fully supported with roles (admin/manager/member) and department scopes. Sharing via expiring links or join codes; activity logs show who viewed/edited tasks. |

## **Success Criteria**

| **Section** | **Details** |
| --- | --- |
| **Performance Goals** | - **OCR Accuracy:** ≥95% text extraction accuracy for meeting minutes.
- **Task Extraction:** Correctly identifies ≥90% of action items and deadlines.
- **Chatbot:** Accurate, task-specific answers.
- **Efficiency:** Staff report faster task assignment and tracking.
- **Reliability:** Handles multiple users and calendar integrations without delays. |

# Use Case 2: Document Analysis. Corrected OCR + Document Summary. Chatbot Query

## **Objective**

To develop a web-based Document Analysis System (with optional mobile support) that processes scanned or digital documents (PDFs, images) for Ekamas Mandiri Group. The system extracts text using OCR, corrects errors, generates summaries, stores documents for search, and enables natural language queries via a chatbot to improve efficiency in accessing and analyzing company documents.

## **Platform Overview**

| **Section** | **Details** | Comments |
| --- | --- | --- |
| **Access Channels** | Access through PKC |  |
| **User Flow** | Users upload documents, view processed results (text, summaries), search archives, and interact with a chatbot for document-specific questions.<br><br>Users select a local folder containing documents, automatically process them into text and summaries, search the archived results, and interact with a chatbot for document-specific questions. | Can user just point to a specific directory in the hard drive without having to upload the files? |

## **Functional Requirements**

| **Section** | **Details** | Comments |
| --- | --- | --- |
| **1. Document Upload and Processing** | - **Supported Formats:** PDF, JPG, PNG, or scanned images.<br>- **Processing Steps:**<br>- OCR extracts text from images/PDFs.<br>- Error correction fixes OCR mistakes (e.g., typos) using AI.<br>- Summarization generates a concise summary (20-50% of original length).<br>- Indexing stores text, summary in a searchable database. | **Possible only when self-hosted.** Supports local folder watch for certain file types (e.g., images, PDFs). Self-hosted friendly. Watch a local folder and process files on-device for privacy. Use OCR with language auto-detect; for clean PDFs, prefer text-extraction over OCR. Provide progress and error logs per file. |
| **2. Customizable Document Categories** | - User define categories (e.g., Contracts, Reports, Invoices).<br>- Categories editable anytime to reflect company needs.<br>- Users assign categories during upload for easier archiving/searching. | **Possible.** Start with free-form tags; later add admin-managed taxonomy with color labels and access rules. Support bulk tagging during import and auto-tag suggestions from document content. |
| **3. Document Summarization** | - **Automatic Summaries:** AI creates summaries focusing on key details (e.g., dates, terms).<br>- **Editable:** Users can adjust summaries manually.<br>- **Length Control:** Set summary length (e.g., 100-200 words short, 300-500 words detailed).<br>- **Goal:** Save ≥50% reading time. | **Possible.** Ground summaries with citations/snippets so users can verify. Provide quick presets (Short/Standard/Detailed). Offer a compare view (original vs summary) before saving. |
| **4. Searchable Document Archive** | - **Search:** Keyword/phrase search across all documents; results show previews with highlighted matches.<br>- **Filters:** By category, date, or tags.<br>- **Indexing:** Fast, Google-like search via database.<br>- **Version Control:** Tracks document updates/re-uploads. | **Possible.** Local index for privacy. Combine keyword + semantic search. Index OCR text, extracted entities (dates, names), and category tags. Keep content-hash versions for traceability and rollback. |
| **5. Chatbot Query System** | - **Queries:** Users ask natural language questions (e.g., “What’s the contract’s expiry date?”).<br>- **Context:** Chatbot uses document content for accurate answers.<br>- **Follow-Ups:** Supports multi-turn conversations.<br>- **Error Handling:** Requests clarification for unclear questions. | **Possible.** Retrieval-augmented responses that quote source lines with links to the document section. Add guardrails to limit to indexed content and ask clarifying questions when ambiguous. |
| **6. Secure User Access** | - **Access Control:** Users set permissions (e.g., who can upload/view/edit).<br>- **Security:** Encrypted storage and transfer.<br>- **Audit Trail:** Logs document access/modifications. | **Makes sense.** Role-based access (admin/editor/viewer). Encryption at rest and in transit. Audit log shows who viewed/edited/exported; export actions can require admin approval for sensitive categories. |
| **7. Export Capabilities** | - **Formats:** Download text, summaries, or query results as docs, PDF, or Excel (for tables).<br>- **Process:** One-click download from document or search page.<br>- **Batch Export:** Option to export multiple documents. | **Makes sense.** Include CSV/Excel for tables, PDF for reports, and redaction tools (mask names/IDs) prior to export. Support bulk export with progress and resumable downloads. |
| **8. Processing Notifications** | - **Error Alerts:** Notifies user of issues (e.g., blurry scan) with re-upload suggestion. | **Makes sense.** In-app alerts plus optional email/Telegram. Provide actionable tips (e.g., increase scan DPI, re-scan specific pages). Include retry button and link to logs. |
| **9. Multi-Language Support**  | - **Languages:** Supports common company languages (e.g., English, Indonesian).<br>- **Validation:** Auto-detects document language for processing. | **Possible.** Auto-detect OCR language; allow manual override. Ensure date/number formats are parsed per locale so summaries and search facets remain accurate. |
| **10. Error Handling and Recovery** | - **OCR Failures:** Prompts re-upload or manual text input for poor scans.<br>- **Database:** Automatic backups prevent data loss.<br>- **Chatbot:** Suggests alternative questions for unanswerable queries. | **Makes sense.** Graceful fallbacks: partial extraction with warnings instead of hard failures. Nightly backups and point-in-time restore. Provide a manual correction UI for OCR errors. |
| **13. Group/Departmental Access**  | - **Permissions:** Authorized user assign department-specific access (e.g., Legal sees only contracts).<br>- **Shared Access:** Teams share documents via codes/links. | **Possible, but not in initial release.** Initial scope will offer basic sharing (per-document or per-folder) without hierarchical inheritance. The full requirement (inheritance Org > Dept > Team, expiring links/join codes, instant revocation, watermarked exports) is planned for a later phase. |

## **Success Criteria**

| **Section** | **Details** |
| --- | --- |
| **Performance Goals** | - OCR: ≥95% text accuracy.
- Summaries: Reduce reading time by ≥50%.
- Chatbot: Accurate, document-specific answers.
- Efficiency: Staff report faster information access.
- Reliability: Handles multiple users without crashes. |

# Use Case 3: Sales Team WA Analysis

## **Objective**

To analyze exported WhatsApp customer chats (TXT files) for Ekamas Mandiri Group’s sales and marketing team. The system uses AI/NLP to detect customer intent, sentiment, and buying signals, then classifies customers into Cold, Warm, or Hot leads. This helps the team prioritize follow-ups and improve conversion efficiency.

---

## **Platform Overview**

| **Section** | **Details** | **Notes** |
| --- | --- | --- |
| **Access Channels** | Access via internal web dashboard or PKC integration. | Mobile support optional for sales team on-the-go. |
| **User Flow** | Users export WhatsApp chat (TXT), upload it into the system, view AI analysis (intent, sentiment, readiness score), and receive follow-up recommendations. | Future option: automate via WhatsApp Business API + CRM. |
| **Confirmation** | Successful analysis generates a report/dashboard notification (in-app or email). | Can also push lead status directly to CRM. |

## **Functional Requirements**

| **Section** | **Details** | Comments |
| --- | --- | --- |
| **1. Chat Upload and Processing** | - **Supported Input:** WhatsApp exported TXT files (initial phase).<br>- **Processing Steps:**<br>• AI reads conversation text.<br>• Detects key terms (price, booking, down payment, mortgage).<br>• Identifies intent (inquiry, interest, negotiation, closing).<br>• Performs sentiment analysis (positive, neutral, negative).<br>• Generates Purchase Readiness Score. | **Initial plan: via Google backup ingestion.** PKC accesses the user's Google backup for WhatsApp and processes it directly. Direct TXT upload remains supported as an alternative. |
| **2. Lead Classification** | Customers are scored on a **1–5 readiness scale** based on AI analysis:<br>• **1:** Very low intent, general browsing only.<br>• **2:** Low intent, some casual questions.<br>• **3:** Medium intent, asking relevant details (e.g., location, facilities).<br>• **4:** High intent, discussing financial aspects (e.g., price, down payment).<br>• **5:** Very high intent, close to decision (e.g., booking, scheduling visit, payment options). | **Possible but harder and will take more time.** We need to define reliable signals/heuristics and evaluation criteria; expect iteration to calibrate scoring thresholds. |
| **3. Dashboard & Reporting** | - **Insights shown:** Customer name, readiness score, key signals, and recommended next step.<br>- **Filters:** By readiness level, sentiment, or date.<br>- **Export:** Report available in PDF/Excel. | **Possible.** Standard dashboards with filters and export. |
| **4. Integration (Future Phase)** | - Optional integration with WhatsApp Business API for real-time data.<br>- Sync readiness scores into CRM for automated lead management. | **Makes sense and possible (future phase).** Subject to WhatsApp Business API/CRM access and compliance. |

## **Success Criteria**

| **Section** | **Details** |
| --- | --- |
| **Performance Goals** | - AI correctly classifies customer readiness with ≥80% accuracy.
- Marketing team saves ≥50% time compared to manual chat reading.
- Sales conversion rate improves by 15–20%.
- Sales team reports improved prioritization and follow-up efficiency.
- System is scalable to API/CRM integration for long-term use. |

### Example Result

| **Customer Name** | **Key Intent Detected** | **Sentiment** | **Readiness Score (1–5)** | **Suggested Action** |
| --- | --- | --- | --- | --- |
| Customer A (John) | Asked about house price and down payment options | Positive | **5** (Very High) | Call immediately, offer site visit and booking slot. |
| Customer B (Maya) | Inquired about location and nearby schools | Neutral | **3** (Medium) | Send brochure + location details, follow up in 3 days. |
| Customer C (Rudi) | General browsing, asked “just looking for info” | Neutral | **1** (Very Low) | Add to nurturing list, send marketing newsletter. |
| Customer D (Anita) | Negotiated discount and asked about mortgage options | Positive | **4** (High) | Schedule meeting with sales manager, prepare financing options. |
| Customer E (Kevin) | Asked about availability but did not respond further | Negative | **2** (Low) | Light follow-up message, check interest before dropping. |