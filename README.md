index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ventorme | Career Planner</title>
  <style>
    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f4f6fb;
      color: #172033;
    }
    header {
      background: #172554;
      color: white;
      padding: 30px 20px;
      text-align: center;
    }
    header p { color: #dbeafe; }
    nav {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
      padding: 16px;
      background: white;
      position: sticky;
      top: 0;
    }
    button {
      border: none;
      padding: 11px 15px;
      border-radius: 8px;
      background: #315bea;
      color: white;
      cursor: pointer;
      font-size: 14px;
    }
    button:hover { opacity: .85; }
    button.secondary { background: #e5eaf5; color: #172033; }
    main {
      max-width: 900px;
      margin: 25px auto;
      padding: 0 16px;
    }
    section.panel {
      background: white;
      padding: 24px;
      margin-bottom: 20px;
      border-radius: 14px;
      box-shadow: 0 4px 18px #1720330b;
    }
    .hidden { display: none !important; }
    input, select, textarea {
      width: 100%;
      padding: 12px;
      margin: 8px 0 14px;
      border: 1px solid #ccd3e0;
      border-radius: 8px;
      font: inherit;
    }
    textarea { resize: vertical; min-height: 80px; }
    label { font-weight: bold; display: block; margin-top: 12px; }
    .muted { color: #647087; }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
      gap: 14px;
    }
    .card {
      border: 1px solid #e2e7f0;
      border-radius: 12px;
      padding: 16px;
      background: #fff;
    }
    .tag {
      display: inline-block;
      padding: 5px 9px;
      border-radius: 20px;
      background: #e9efff;
      color: #2446b0;
      font-size: 12px;
    }
    .task {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 12px 0;
      border-bottom: 1px solid #edf0f5;
    }
    .task input { width: auto; margin: 0; }
    .task span { flex: 1; overflow-wrap: anywhere; }
    .done { text-decoration: line-through; color: #788398; }
    .danger { background: #dc3545; }
    .stats {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
      gap: 12px;
      margin: 20px 0;
    }
    .stat {
      background: #edf2ff;
      padding: 16px;
      border-radius: 10px;
    }
    .stat strong { display: block; font-size: 24px; margin-bottom: 5px; }
    .result {
      background: #f0f5ff;
      border-radius: 10px;
      padding: 16px;
      margin-top: 16px;
    }
    footer {
      text-align: center;
      padding: 24px;
      color: #647087;
    }
    @media (max-width: 500px) {
      nav button { flex: 1 1 40%; }
      section.panel { padding: 17px; }
    }
  </style>
</head>
<body>
  <header>
    <h1>Ventorme</h1>
    <p>Discover your future. Build your path.</p>
  </header>

  <nav>
    <button onclick="showPage('home')">Dashboard</button>
    <button onclick="showPage('quiz')">Career Quiz</button>
    <button onclick="showPage('careers')">Careers</button>
    <button onclick="showPage('universities')">Universities</button>
    <button onclick="showPage('tasks')">My Tasks</button>
    <button onclick="showPage('settings')">Settings</button>
  </nav>

  <main>
    <section id="home" class="panel">
      <h2 id="greeting">Welcome to Ventorme!</h2>
      <p class="muted">Your personal space for career exploration and future planning.</p>

      <div class="stats">
        <div class="stat"><strong id="taskCount">0</strong>Pending tasks</div>
        <div class="stat"><strong id="uniCount">0</strong>Saved universities</div>
        <div class="stat"><strong id="careerCount">0</strong>Saved careers</div>
      </div>

      <button onclick="showPage('quiz')">Discover your career</button>
      <button class="secondary" onclick="showPage('tasks')">Plan your next step</button>

      <h3>Your career recommendation</h3>
      <div id="homeRecommendation" class="result">
        Take the career quiz to discover careers that may suit your interests.
      </div>

      <h3>Upcoming tasks</h3>
      <div id="homeTasks"></div>
    </section>

    <section id="quiz" class="panel hidden">
      <h2>Career Discovery Quiz</h2>
      <p class="muted">Answer these questions to explore possible career directions.</p>

      <form id="quizForm">
        <label for="interest">1. What interests you most?</label>
        <select id="interest" required>
          <option value="">Choose an answer</option>
          <option value="technology">Technology and programming</option>
          <option value="business">Business and leadership</option>
          <option value="science">Science and research</option>
          <option value="creative">Art and creative work</option>
          <option value="people">Psychology and helping people</option>
          <option value="law">Law, justice and investigation</option>
        </select>

        <label for="strength">2. What is one of your strengths?</label>
        <select id="strength" required>
          <option value="">Choose an answer</option>
          <option value="logic">Logical thinking</option>
          <option value="communication">Communication</option>
          <option value="creativity">Creativity</option>
          <option value="analysis">Research and analysis</option>
          <option value="leadership">Leadership and organization</option>
        </select>

        <label for="environment">3. What work environment sounds interesting?</label>
        <select id="environment" required>
          <option value="">Choose an answer</option>
          <option value="independent">Independent project work</option>
          <option value="team">Working with a team</option>
          <option value="research">Research and experiments</option>
          <option value="people">Working directly with people</option>
        </select>

        <label for="goal">4. What is a future goal? (optional)</label>
        <input id="goal" placeholder="For example: study abroad">

        <button type="submit">Get my recommendations</button>
        <button type="button" class="secondary" onclick="resetQuiz()">Reset quiz</button>
      </form>

      <div id="quizResult" aria-live="polite"></div>
    </section>

    <section id="careers" class="panel hidden">
      <h2>Explore Careers</h2>
      <p class="muted">Search career paths, learn about them and save your favorites.</p>
      <input id="careerSearch" placeholder="Search careers..." oninput="renderCareers()">
      <select id="careerCategory" onchange="renderCareers()">
        <option value="all">All categories</option>
        <option value="technology">Technology</option>
        <option value="business">Business</option>
        <option value="science">Science</option>
        <option value="creative">Creative</option>
        <option value="people">People and society</option>
        <option value="law">Law and justice</option>
      </select>
      <div id="careerList" class="grid"></div>
      <h3>Saved careers</h3>
      <div id="savedCareers" class="grid"></div>
    </section>

    <section id="universities" class="panel hidden">
      <h2>University Shortlist</h2>
      <p class="muted">Keep track of universities and programs you want to research.</p>

      <form id="universityForm">
        <label for="uniName">University name</label>
        <input id="uniName" placeholder="University name" required>

        <label for="uniCountry">Country</label>
        <input id="uniCountry" placeholder="Country" required>

        <label for="uniProgram">Program or major</label>
        <input id="uniProgram" placeholder="For example: Computer Science">

        <label for="uniStatus">Application status</label>
        <select id="uniStatus">
          <option>Interested</option>
          <option>Researching</option>
          <option>Preparing application</option>
          <option>Applied</option>
          <option>Accepted</option>
        </select>

        <label for="uniNotes">Notes</label>
        <textarea id="uniNotes" placeholder="Deadlines, requirements, scholarships..."></textarea>

        <button type="submit">Add university</button>
      </form>

      <h3>My universities</h3>
      <div id="universityList" class="grid"></div>
    </section>

    <section id="tasks" class="panel hidden">
      <h2>My Task Planner</h2>
      <p class="muted">Turn your goals into manageable steps.</p>

      <form id="taskForm">
        <label for="taskInput">Task</label>
        <input id="taskInput" placeholder="For example: Research IELTS requirements" required>

        <label for="taskDate">Due date (optional)</label>
        <input id="taskDate" type="date">

        <button type="submit">Add task</button>
      </form>

      <div>
        <button class="secondary" onclick="setTaskFilter('all')">All</button>
        <button class="secondary" onclick="setTaskFilter('pending')">Pending</button>
        <button class="secondary" onclick="setTaskFilter('done')">Completed</button>
      </div>

      <div id="taskList"></div>
      <button class="danger" onclick="clearCompletedTasks()">Clear completed tasks</button>
    </section>

    <section id="settings" class="panel hidden">
      <h2>Settings</h2>

      <form id="settingsForm">
        <label for="userName">Your name</label>
        <input id="userName" placeholder="Enter your name">

        <label for="studyStage">Current study stage</label>
        <select id="studyStage">
          <option>School student</option>
          <option>Preparing for university</option>
          <option>University student</option>
          <option>Exploring career options</option>
        </select>

        <label for="userInterests">Interests</label>
        <textarea id="userInterests" placeholder="Technology, business, science..."></textarea>

        <button type="submit">Save settings</button>
      </form>

      <h3>Data management</h3>
      <p class="muted">Your information is saved in this browser on this device.</p>
      <button class="danger" onclick="clearAllData()">Delete all app data</button>
    </section>
  </main>

  <footer>
    <p>Ventorme — Your future starts with one step.</p>
    <p>Personal planning tool. Career suggestions are for exploration, not professional assessments.</p>
  </footer>

  <script>
    const CAREERS = [
      {id:"software",name:"Software Engineer",category:"technology",description:"Design, build and maintain software, applications and digital tools.",skills:"Programming, logic, problem-solving"},
      {id:"data",name:"Data Analyst",category:"technology",description:"Study data to identify patterns and support decisions.",skills:"Statistics, spreadsheets, analytical thinking"},
      {id:"ai",name:"Machine Learning Engineer",category:"technology",description:"Develop systems that learn patterns from data.",skills:"Programming, mathematics, statistics"},
      {id:"cyber",name:"Cybersecurity Specialist",category:"technology",description:"Help protect systems, networks and information.",skills:"Networking, investigation, problem-solving"},
      {id:"business",name:"Business Analyst",category:"business",description:"Understand business problems and suggest improvements.",skills:"Analysis, communication, organization"},
      {id:"finance",name:"Financial Analyst",category:"business",description:"Analyze financial information to support planning.",skills:"Mathematics, economics, attention to detail"},
      {id:"marketing",name:"Marketing Specialist",category:"business",description:"Research audiences and develop communication strategies.",skills:"Creativity, research, communication"},
      {id:"scientist",name:"Research Scientist",category:"science",description:"Investigate questions through research and experiments.",skills:"Research, critical thinking, patience"},
      {id:"biotech",name:"Biotechnology Specialist",category:"science",description:"Apply biology to develop useful technologies and solutions.",skills:"Biology, laboratory skills, analysis"},
      {id:"designer",name:"Graphic Designer",category:"creative",description:"Create visual communication, layouts and digital designs.",skills:"Visual thinking, design tools, creativity"},
      {id:"writer",name:"Content Writer",category:"creative",description:"Communicate ideas through clear and engaging writing.",skills:"Writing, research, language"},
      {id:"psychologist",name:"Psychologist",category:"people",description:"Study behavior and help people understand psychological challenges.",skills:"Listening, research, empathy"},
      {id:"teacher",name:"Teacher",category:"people",description:"Help students learn, grow and develop skills.",skills:"Communication, patience, planning"},
      {id:"lawyer",name:"Lawyer",category:"law",description:"Research legal questions and help people understand their rights.",skills:"Reasoning, writing, research"},
      {id:"investigator",name:"Investigator",category:"law",description:"Gather and evaluate information to clarify events and evidence.",skills:"Observation, analysis, attention to detail"}
    ];

    const STORAGE_KEY = "ventormeAppDataV1";

    function loadData() {
      try {
        return JSON.parse(localStorage.getItem(STORAGE_KEY)) || {};
      } catch {
        return {};
      }
    }

    let data = Object.assign({
      name: "",
      stage: "School student",
      interests: "",
      tasks: [],
      universities: [],
      savedCareers: [],
      recommendation: null
    }, loadData());

    let taskFilter = "all";

    function saveData() {
      try {
        localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
      } catch {
        alert("Your browser could not save the data. Check browser storage settings.");
      }
      renderAll();
    }

    function escapeHTML(value) {
      return String(value ?? "").replace(/[&<>"']/g, char => ({
        "&":"&amp;",
        "<":"&lt;",
        ">":"&gt;",
        '"':"&quot;",
        "'":"&#39;"
      })[char]);
    }

    function showPage(page) {
      document.querySelectorAll("main > section").forEach(section => {
        section.classList.add("hidden");
      });
      const target = document.getElementById(page);
      if (target) target.classList.remove("hidden");
      renderAll();
      window.scrollTo({top:0,behavior:"smooth"});
    }

    function renderDashboard() {
      document.getElementById("greeting").textContent =
        data.name ? `Welcome back, ${data.name}!` : "Welcome to Ventorme!";

      document.getElementById("taskCount").textContent =
        data.tasks.filter(task => !task.done).length;
      document.getElementById("uniCount").textContent = data.universities.length;
      document.getElementById("careerCount").textContent = data.savedCareers.length;

      const rec = document.getElementById("homeRecommendation");
      if (data.recommendation) {
        const names = data.recommendation.careers.map(c => escapeHTML(c.name)).join(", ");
        rec.innerHTML = `<strong>Suggested career directions:</strong><p>${names}</p>
          <p>${escapeHTML(data.recommendation.goal || "Keep exploring your options.")}</p>
          <button onclick="showPage('careers')">Explore careers</button>`;
      } else {
        rec.textContent = "Take the career quiz to discover careers that may match your interests.";
      }

      const pending = data.tasks.filter(task => !task.done).slice(0,5);
      document.getElementById("homeTasks").innerHTML = pending.length
        ? pending.map(task => `<div class="task"><span>${escapeHTML(task.text)}</span>
            ${task.date ? `<small>${escapeHTML(task.date)}</small>` : ""}</div>`).join("")
        : '<p class="muted">No pending tasks. Add a task to get started.</p>';
    }

    function submitQuiz(event) {
      event.preventDefault();

      const interest = document.getElementById("interest").value;
      const strength = document.getElementById("strength").value;
      const environment = document.getElementById("environment").value;
      const goal = document.getElementById("goal").value.trim();

      let results = CAREERS.filter(career => career.category === interest);

      const strengthMatches = {
        logic: ["software","ai","cyber","data"],
        communication: ["marketing","teacher","lawyer","writer"],
        creativity: ["designer","marketing","software","writer"],
        analysis: ["data","business","scientist","investigator"],
        leadership: ["business","marketing","teacher","lawyer"]
      };

      const preferredIds = strengthMatches[strength] || [];
      results.sort((a,b) =>
        Number(preferredIds.includes(b.id)) - Number(preferredIds.includes(a.id))
      );

      if (environment === "research") {
        results.sort((a,b) =>
          Number(["scientist","data","biotech"].includes(b.id)) -
          Number(["scientist","data","biotech"].includes(a.id))
        );
      }

      results = results.slice(0,4);
      if (!results.length) results = CAREERS.slice(0,4);

      data.recommendation = {careers:results,goal};
      saveData();

      document.getElementById("quizResult").innerHTML = `
        <div class="result">
          <h3>Your career directions</h3>
          <p>These suggestions are a starting point based on your answers.</p>
          <div class="grid">
            ${results.map(career => `<div class="card">
              <span class="tag">${escapeHTML(career.category)}</span>
              <h4>${escapeHTML(career.name)}</h4>
              <p>${escapeHTML(career.description)}</p>
              <p class="muted"><strong>Useful skills:</strong> ${escapeHTML(career.skills)}</p>
              <button onclick="toggleSavedCareer('${career.id}')">
                ${data.savedCareers.includes(career.id) ? "Remove saved career" : "Save career"}
              </button>
            </div>`).join("")}
          </div>
          <p>Remember: a quiz cannot determine your future. Explore these careers and compare them with your own interests.</p>
          <button onclick="showPage('careers')">Explore all careers</button>
          <button class="secondary" onclick="resetQuiz()">Retake quiz</button>
        </div>`;
    }

    function resetQuiz() {
      document.getElementById("quizForm").reset();
      document.getElementById("quizResult").innerHTML = "";
    }

    function renderCareers() {
      const search = (document.getElementById("careerSearch")?.value || "").toLowerCase();
      const category = document.getElementById("careerCategory")?.value || "all";

      const results = CAREERS.filter(career =>
        (category === "all" || career.category === category) &&
        (career.name.toLowerCase().includes(search) ||
         career.description.toLowerCase().includes(search) ||
         career.skills.toLowerCase().includes(search))
      );

      document.getElementById("careerList").innerHTML = results.length
        ? results.map(career => `
          <div class="card">
            <span class="tag">${escapeHTML(career.category)}</span>
            <h3>${escapeHTML(career.name)}</h3>
            <p>${escapeHTML(career.description)}</p>
            <p class="muted"><strong>Skills:</strong> ${escapeHTML(career.skills)}</p>
            <button onclick="toggleSavedCareer('${career.id}')">
              ${data.savedCareers.includes(career.id) ? "★ Saved — remove" : "☆ Save career"}
            </button>
            <button class="secondary" onclick="addCareerTask('${career.id}')">Add research task</button>
          </div>`).join("")
        : '<p>No careers found. Try another search or category.</p>';

      const saved = CAREERS.filter(career => data.savedCareers.includes(career.id));
      document.getElementById("savedCareers").innerHTML = saved.length
        ? saved.map(career => `<div class="card">
            <h3>${escapeHTML(career.name)}</h3>
            <p>${escapeHTML(career.description)}</p>
            <button class="danger" onclick="toggleSavedCareer('${career.id}')">Remove</button>
          </div>`).join("")
        : '<p class="muted">You have not saved any careers yet.</p>';
    }

    function toggleSavedCareer(id) {
      if (data.savedCareers.includes(id)) {
        data.savedCareers = data.savedCareers.filter(item => item !== id);
      } else {
        data.savedCareers.push(id);
      }
      saveData();
    }

    function addCareerTask(id) {
      const career = CAREERS.find(item => item.id === id);
      if (!career) return;
      data.tasks.push({id:makeId(),text:`Research career: ${career.name}`,date:"",done:false});
      saveData();
      alert("Research task added to your planner.");
    }

    function makeId() {
      return Date.now().toString(36) + Math.random().toString(36).slice(2,8);
    }

    function addUniversity(event) {
      event.preventDefault();
      const university = {
        id:makeId(),
        name:document.getElementById("uniName").value.trim(),
        country:document.getElementById("uniCountry").value.trim(),
        program:document.getElementById("uniProgram").value.trim(),
        status:document.getElementById("uniStatus").value,
        notes:document.getElementById("uniNotes").value.trim()
      };

      if (!university.name || !university.country) {
        alert("Please enter the university name and country.");
        return;
      }

      data.universities.push(university);
      document.getElementById("universityForm").reset();
      saveData();
    }

    function renderUniversities() {
      const list = document.getElementById("universityList");
      list.innerHTML = data.universities.length
        ? data.universities.map(uni => `
          <div class="card">
            <h3>${escapeHTML(uni.name)}</h3>
            <p>${escapeHTML(uni.country)}</p>
            ${uni.program ? `<p><strong>Program:</strong> ${escapeHTML(uni.program)}</p>` : ""}
            <label>Status</label>
            <select onchange="updateUniversityStatus('${uni.id}',this.value)">
              ${["Interested","Researching","Preparing application","Applied","Accepted"].map(status =>
                `<option ${uni.status === status ? "selected" : ""}>${status}</option>`
              ).join("")}
            </select>
            ${uni.notes ? `<p><strong>Notes:</strong> ${escapeHTML(uni.notes)}</p>` : ""}
            <button class="danger" onclick="deleteUniversity('${uni.id}')">Remove</button>
          </div>`).join("")
        : '<p class="muted">Your shortlist is empty. Add a university to start planning.</p>';
    }

    function updateUniversityStatus(id,status) {
      const uni = data.universities.find(item => item.id === id);
      if (!uni) return;
      uni.status = status;
      saveData();
    }

    function deleteUniversity(id) {
      data.universities = data.universities.filter(uni => uni.id !== id);
      saveData();
    }

    function addTask(event) {
      event.preventDefault();
      const input = document.getElementById("taskInput");
      const text = input.value.trim();
      const date = document.getElementById("taskDate").value;

      if (!text) {
        alert("Please enter a task.");
        return;
      }

      data.tasks.push({id:makeId(),text,date,done:false});
      document.getElementById("taskForm").reset();
      saveData();
    }

    function toggleTask(id) {
      const task = data.tasks.find(item => item.id === id);
      if (!task) return;
      task.done = !task.done;
      saveData();
    }

    function deleteTask(id) {
      data.tasks = data.tasks.filter(task => task.id !== id);
      saveData();
    }

    function setTaskFilter(filter) {
      taskFilter = filter;
      renderTasks();
    }

    function renderTasks() {
      const tasks = data.tasks.filter(task =>
        taskFilter === "all" ||
        (taskFilter === "pending" && !task.done) ||
        (taskFilter === "done" && task.done)
      );

      document.getElementById("taskList").innerHTML = tasks.length
        ? tasks.map(task => `
          <div class="task">
            <input type="checkbox" aria-label="Mark task completed"
              ${task.done ? "checked" : ""}
              onchange="toggleTask('${task.id}')">
            <span class="${task.done ? "done" : ""}">${escapeHTML(task.text)}
              ${task.date ? `<br><small class="muted">Due: ${escapeHTML(task.date)}</small>` : ""}
            </span>
            <button class="danger" onclick="deleteTask('${task.id}')">Delete</button>
          </div>`).join("")
        : '<p class="muted">No tasks in this category.</p>';
    }

    function clearCompletedTasks() {
      if (!data.tasks.some(task => task.done)) {
        alert("There are no completed tasks to clear.");
        return;
      }
      if (confirm("Delete all completed tasks?")) {
        data.tasks = data.tasks.filter(task => !task.done);
        saveData();
      }
    }

    function saveSettings(event) {
      event.preventDefault();
      data.name = document.getElementById("userName").value.trim();
      data.stage = document.getElementById("studyStage").value;
      data.interests = document.getElementById("userInterests").value.trim();
      saveData();
      alert("Your settings have been saved.");
    }

    function loadSettings() {
      document.getElementById("userName").value = data.name;
      document.getElementById("studyStage").value = data.stage;
      document.getElementById("userInterests").value = data.interests;
    }

    function clearAllData() {
      if (!confirm("This will permanently remove your tasks, universities, saved careers and settings from this browser. Continue?")) {
        return;
      }

      localStorage.removeItem(STORAGE_KEY);
      data = {
        name:"",
        stage:"School student",
        interests:"",
        tasks:[],
        universities:[],
        savedCareers:[],
        recommendation:null
      };

      resetQuiz();
      loadSettings();
      renderAll();
      showPage("home");
      alert("App data has been cleared.");
    }

    function renderAll() {
      renderDashboard();
      renderCareers();
      renderUniversities();
      renderTasks();
      loadSettings();
    }

    document.getElementById("quizForm").addEventListener("submit", submitQuiz);
    document.getElementById("taskForm").addEventListener("submit", addTask);
    document.getElementById("universityForm").addEventListener("submit", addUniversity);
    document.getElementById("settingsForm").addEventListener("submit", saveSettings);

    renderAll();
  </script>
</body>
</html>

