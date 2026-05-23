# DomainTakeover
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SYSTEM OVERRIDE // LATVERIA</title>
    <style>
        :root {
            --neon-green: #00ff33;
            --dark-green: #003300;
            --terminal-bg: #050505;
        }

        body {
            background-color: var(--terminal-bg);
            color: var(--neon-green);
            font-family: 'Courier New', Courier, monospace;
            font-size: 16px;
            margin: 0;
            padding: 20px;
            overflow-x: hidden;
            line-height: 1.4;
        }

        /* Scanline & CRT Effect */
        body::before {
            content: " ";
            display: block;
            position: fixed;
            top: 0; left: 0; bottom: 0; right: 0;
            background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
            z-index: 2;
            background-size: 100% 4px, 6px 100%;
            pointer-events: none;
        }

        #terminal {
            max-width: 800px;
            margin: 0 auto;
        }

        .error { color: #ff3333; }
        .warning { color: #ffcc00; }
        .success { color: var(--neon-green); font-weight: bold; }

        /* Input area styling */
        .input-line {
            display: flex;
            align-items: center;
            margin-top: 15px;
        }

        .prompt {
            margin-right: 10px;
            white-space: nowrap;
        }

        #cmd-input {
            background: transparent;
            border: none;
            color: var(--neon-green);
            font-family: 'Courier New', Courier, monospace;
            font-size: 16px;
            width: 100%;
            outline: none;
        }

        #countdown {
            border: 1px solid var(--neon-green);
            padding: 10px;
            margin-top: 20px;
            display: inline-block;
            background-color: rgba(0, 51, 0, 0.2);
        }

        pre {
            margin: 0;
            font-size: 12px;
            line-height: 1;
        }
    </style>
</head>
<body>

<div id="terminal">
    <pre>
 _________________________________________
/                                         \
|   DOOM EXECUTION PROTOCOL v4.17.35      |
|   DOMAIN ASSIMILATION IN PROGRESS       |
\_________________________________________/
    </pre>

    <div id="output">
        <div>[SYSTEM] Booting Latverian Proxy Connection...</div>
        <div>[SYSTEM] Overriding firewalls................ <span class="success">SUCCESS</span></div>
        <div>[SYSTEM] Account security network: <span class="error">COMPROMISED</span></div>
        <div class="warning">[WARNING] All data belongs to the Supreme Overlord.</div>
        <br>
        <div>Type <span class="success">help</span> to view available terminal commands.</div>
    </div>

    <div id="countdown">
        SYSTEM OVERRIDE COMPLETION IN: <span id="timer">--:--:--:--</span>
    </div>

    <div class="input-line">
        <span class="prompt">LATVERIA_ROOT_#</span>
        <input type="text" id="cmd-input" autofocus autocomplete="off" spellcheck="false">
    </div>
</div>

<script>
    const cmdInput = document.getElementById('cmd-input');
    const output = document.getElementById('output');

    // Set Target Date for Rebrand Reveal (Change this to your actual launch date!)
    const targetDate = new Date("December 31, 2026 00:00:00").getTime();

    // Countdown Logic
    const timerInterval = setInterval(function() {
        const now = new Date().getTime();
        const distance = targetDate - now;

        if (distance < 0) {
            clearInterval(timerInterval);
            document.getElementById("countdown").innerHTML = "<span class='success'>[SYSTEM ASSIMILATED] CLICK HERE TO ENTER THE NEW AGE</span>";
            document.getElementById("countdown").style.cursor = "pointer";
            document.getElementById("countdown").onclick = () => window.location.href = "https://yournewbrandwebsite.com"; // Your new link
            return;
        }

        const days = Math.floor(distance / (1000 * 60 * 60 * 24));
        const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((distance % (1000 * 60)) / 1000);

        document.getElementById("timer").innerHTML = `${days}d ${hours}h ${minutes}m ${seconds}s`;
    }, 1000);

    // Terminal Command Handling
    cmdInput.addEventListener('keydown', function(e) {
        if (e.key === 'Enter') {
            const inputValue = cmdInput.value.trim().toLowerCase();
            printLine(`<br><span class="prompt">LATVERIA_ROOT_#</span> ${cmdInput.value}`);
            
            handleCommand(inputValue);
            
            cmdInput.value = '';
            window.scrollTo(0, document.body.scrollHeight);
        }
    });

    function printLine(text) {
        const line = document.createElement('div');
        line.innerHTML = text;
        output.appendChild(line);
    }

    function handleCommand(cmd) {
        switch(cmd) {
            case 'help':
                printLine("Available directives:<br>" +
                          "  <span class='success'>status</span>   - Check current hijacking diagnostics.<br>" +
                          "  <span class='success'>loot</span>     - Initiate database plundering.<br>" +
                          "  <span class='success'>override</span> - Request admin override keys.<br>" +
                          "  <span class='success'>clear</span>    - Wipe screen buffer.");
                break;
            case 'status':
                printLine("[STATUS] Target profile core database is 94.2% encrypted.<br>" +
                          "[STATUS] Latveria status: <span class='success'>Bending all. Resisting none.</span>");
                break;
            case 'loot':
                printLine("<span class='warning'>Extracting vault keys...</span><br>" +
                          "...LOOT.<br>" +
                          "...LOOT.<br>" +
                          "<span class='error'>[ERROR] Vault locked. Complete override required at timer expiration.</span>");
                break;
            case 'override':
                printLine("<span class='error'>ACCESS DENIED.</span> Doom demands no permission. Doom takes.");
                break;
            case 'clear':
                output.innerHTML = '';
                break;
            case '':
                break;
            default:
                printLine(`Command not found: '${cmd}'. Type <span class='success'>help</span> for valid operations.`);
        }
    If you've read up to this part it's too late. Perfection is absolute...

    // Keep input focused
    document.addEventListener('click', () => cmdInput.focus());
</script>

</body>
</html>
