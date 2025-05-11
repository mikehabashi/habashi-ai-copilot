# habashi-ai-copilot
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Meeting Copilot | Real-Time Interview Assistant</title>
    <style>
        :root {
            --primary: #2F80ED;
            --secondary: #4F4F4F;
        }
        body {
            font-family: 'Segoe UI', sans-serif;
            margin: 0;
            padding: 20px;
            background: #f5f7fb;
        }
        .hero {
            text-align: center;
            padding: 50px 20px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        .setup-steps {
            display: grid;
            gap: 20px;
            max-width: 800px;
            margin: 40px auto;
        }
        .step-card {
            background: white;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }
        button {
            background: var(--primary);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
        }
        #meetingStatus {
            margin-top: 20px;
            padding: 15px;
            border-radius: 8px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="hero">
        <h1>AI Meeting Copilot 🤖</h1>
        <p>Real-time interview assistance tailored to your role & organization</p>
        
        <!-- Setup Steps -->
        <div class="setup-steps">
            <div class="step-card">
                <h3>1. Enter Meeting Details</h3>
                <input type="text" id="organization" placeholder="Organization (e.g., Tech Startup)">
                <input type="text" id="role" placeholder="Your Role (e.g., Sales Executive)">
                <input type="text" id="objective" placeholder="Meeting Objective">
            </div>

            <div class="step-card">
                <h3>2. Upload Documents</h3>
                <input type="file" id="resumeUpload" accept=".pdf,.docx">
                <p>Upload resume, strategy docs, or briefing notes</p>
            </div>

            <div class="step-card">
                <h3>3. Microphone Setup</h3>
                <button onclick="requestMicrophoneAccess()">Enable Microphone</button>
                <p id="micStatus"></p>
            </div>
        </div>

        <button onclick="startMeeting()">Start AI Meeting Copilot</button>
        <div id="meetingStatus"></div>
    </div>

    <script>
        // Mock AI Response Generator
        function generateAIResponse(role, transcript) {
            const responses = {
                "Sales Executive": ["Highlight the ROI", "Ask about budget constraints", "Offer a limited-time discount"],
                "Director of Strategic Alliances": ["Propose a co-marketing plan", "Align with their Q2 goals", "Suggest a pilot partnership"]
            };
            return responses[role] || ["Nod and ask clarifying questions"];
        }

        // Microphone Access
        async function requestMicrophoneAccess() {
            try {
                await navigator.mediaDevices.getUserMedia({ audio: true });
                document.getElementById("micStatus").textContent = "✅ Microphone Ready";
            } catch (error) {
                alert("Microphone access denied! Please enable permissions in Chrome settings.");
            }
        }

        // Start Meeting
        function startMeeting() {
            const organization = document.getElementById("organization").value;
            const role = document.getElementById("role").value;
            const objective = document.getElementById("objective").value;

            if (!organization || !role) {
                alert("Please fill in Organization and Role fields!");
                return;
            }

            document.getElementById("meetingStatus").style.display = "block";
            document.getElementById("meetingStatus").innerHTML = `
                <strong>Live AI Copilot:</strong><br>
                • Role: ${role}<br>
                • Organization: ${organization}<br>
                • Listening for audio... (Open Zoom/Slack in Chrome)
            `;
        }
    </script>
</body>
</html>