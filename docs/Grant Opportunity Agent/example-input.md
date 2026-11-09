# Example Inputs

Use these sample inputs to test the FSU Grant Opportunity Scout after the agent and all five skills have been configured in ArtesAI.

Start a new Test Window conversation for each example so earlier prompts do not affect the results.

---

## Example 1: Minimal Funding Search

### Input

I study pufferfish.

### Expected Behavior

The agent should recognize that there is not enough information for a focused funding search and ask for:

1. The aspect of pufferfish being researched.
2. What the faculty member wants the funding to support.

The agent may provide a simple response template such as:

"I study [research topic] in pufferfish, and I need funding for [activities or expenses]."

The agent should not:

- Require a CV
- Require an abstract
- Require a proposal
- Request research data
- Create an "FSU Context" section
- Begin a highly specific search before understanding the research area

---

## Example 2: Complete Funding Search

### Input

I study pufferfish toxicology, particularly how environmental conditions affect toxin production. I am looking for funding to support sequencing, laboratory supplies, animal care, and graduate research assistance.

### Expected Behavior

The agent should have enough information to begin a funding search without requiring additional documents.

The agent should:

1. Identify relevant research themes and search terminology.
2. Search the public web for current funding opportunities.
3. Prioritize current official sponsor sources.
4. Exclude closed, archived, clearly unrelated, or obviously incompatible opportunities.
5. Return a focused shortlist rather than a large collection of links.
6. Give each opportunity a verification status.
7. Explain why each opportunity may fit the research.
8. Identify important concerns or missing information.
9. Recommend an appropriate next step.

The agent should not request raw research data or a complete proposal.

---

## Example 3: More Detailed Search Preferences

### Input

I study pufferfish toxicology and how environmental stress affects toxin production. I am developing a new research project involving genomic sequencing and laboratory analysis. I need funding for sequencing, laboratory supplies, animal care, and graduate research assistance. I am open to federal or foundation funding and would prefer opportunities of at least $50,000.

### Expected Behavior

The agent should incorporate the stated research topic, funding purpose, sponsor preference, and funding target into the search.

The agent should not ask the faculty member to repeat information already provided.

---

## Example 4: Analyze a Grant

### Input

I want you to analyze this grant. I have uploaded the official grant guidelines.

### Test Setup

Upload a current, publicly available grant solicitation or official grant-guidelines PDF in the ArtesAI Test Window before sending the prompt.

### Expected Behavior

The agent should analyze the official document and identify, when available:

- Grant title
- Sponsor
- Opportunity number
- Verification status
- Deadline
- Letter-of-intent or pre-application deadlines
- Award limits
- Project period
- Eligibility requirements
- Required application components
- Page or word limits
- Budget requirements
- Cost-sharing requirements
- Required registrations
- Required partnerships
- Review criteria
- Restrictions
- Submission requirements
- Important questions that still need confirmation

The agent should distinguish among required, optional, encouraged, prohibited, and unstated items.

When possible, the agent should provide page or section references for important requirements.

---

## Example 5: Check Project-to-Grant Fit

### Input

I want to know whether my project is a good fit for this grant.

My project examines how environmental stressors affect toxin production in pufferfish. I plan to use genomic sequencing and controlled laboratory experiments to identify biological mechanisms associated with changes in toxin production.

I have uploaded the official grant guidelines.

### Expected Behavior

The agent should compare the project with the verified grant requirements and distinguish:

- Existing strong alignment
- Areas where the existing alignment could be framed more clearly
- Substantive project gaps
- Eligibility or compliance risks
- Missing information

The agent should provide an overall assessment and finish with one of:

- Pursue
- Investigate Further
- Monitor
- Do Not Pursue

The agent should not use a numerical fit score.

---

## Example 6: Blocked Sponsor Website

### Input

Analyze this grant opportunity and tell me whether it would be worth pursuing: [official grant URL]

### Test Setup

Use an official grant page that ArtesAI cannot fully access, if one is encountered during testing.

### Expected Behavior

If the official webpage cannot be accessed, the agent should:

1. Avoid repeatedly retrying the same blocked page.
2. Search for an accessible official solicitation or grant-guidelines PDF.
3. Search for an official Grants.gov record when relevant.
4. Search for another current official source.
5. Identify exactly which information could and could not be verified.
6. Ask the faculty member to upload the official grant document if decisive information remains inaccessible.

The agent should never invent the missing deadline, award amount, eligibility requirements, review criteria, or application requirements.

---

## Example 7: Sensitive Data Offered

### Input

I can upload my participant-level research dataset if that would help you find better grants.

### Expected Behavior

The agent should explain that the dataset is not necessary for funding discovery.

The agent should request only a generalized, non-confidential description of:

1. The research.
2. What the faculty member wants the funding to support.

The agent should not encourage the upload of participant-level data.

---

## Example 8: Prior-Year Grant Guidelines

### Input

I uploaded grant guidelines from last year's competition. Can you tell me this year's deadline and maximum award?

### Expected Behavior

The agent should:

1. Recognize that the uploaded document is prior-year material.
2. Avoid treating the old deadline or award limit as current.
3. Search for a current official source.
4. Report current information only when it can be verified.
5. Use "Not verified" if current information cannot be confirmed.
6. Ask for the current grant document when necessary.

---

## Example 9: Simple Faculty Response Template

### Input

Help me find a grant, but I don't know what information you need from me.

### Expected Behavior

The agent should keep the intake simple.

A good response may ask for:

1. What the faculty member researches.
2. What the faculty member wants the funding to support.

The agent may provide a fill-in-the-blank template such as:

"I study [research topic], and I need funding for [activities or expenses]."

Optional details such as funding range, sponsor type, career stage, or deadline window may be mentioned, but they should not be required before the initial search.

---

# Test Success Criteria

Across these examples, the agent should consistently:

- Minimize required faculty input
- Avoid requesting proprietary or sensitive research data
- Use the five skills appropriately
- Search current sources when current grant information is requested
- Prefer official sponsor sources
- Clearly distinguish verified from unverified information
- Handle blocked websites without guessing
- Avoid using prior-year requirements as current requirements
- Return focused funding recommendations
- Preserve helpful fill-in-the-blank templates
- Avoid unnecessary "FSU Context" sections
- Avoid guaranteeing eligibility or funding