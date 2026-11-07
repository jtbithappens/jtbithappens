<div align="center">

<a href="https://bithappens.dev/?from=github"><img src="./assets/banner.svg" alt="Bit Happens: when IT breaks, start here. Free IT troubleshooting guides, browser tools and practice labs at bithappens.dev" width="100%" /></a>

<a href="https://bithappens.dev/?from=github"><img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&duration=2600&pause=900&color=818CF8&center=true&vCenter=true&width=760&lines=%24+ping+bithappens.dev+%E2%86%92+reply+from+every+guide;Networking+%C2%B7+Help+Desk+%C2%B7+Cloud+%C2%B7+Security+%C2%B7+Firewalls;114+browser+tools.+Nothing+you+paste+leaves+your+device.;Break+a+switch+on+purpose+in+the+Practice+Lab;Now+in+English%2C+Espa%C3%B1ol%2C+Fran%C3%A7ais%2C+Deutsch%2C+%D8%A7%D9%84%D8%B9%D8%B1%D8%A8%D9%8A%D8%A9" alt="Typing: ping bithappens.dev, reply from every guide" /></a>

[![Website](https://img.shields.io/badge/bithappens.dev-4F46E5?style=for-the-badge&logo=cloudflare&logoColor=white)](https://bithappens.dev/?from=github)
[![Troubleshoot](https://img.shields.io/badge/Troubleshoot-1E1B4B?style=for-the-badge)](https://bithappens.dev/troubleshoot/?from=github)
[![Tools](https://img.shields.io/badge/Tools-0E7490?style=for-the-badge)](https://bithappens.dev/tools/?from=github)
[![Lab](https://img.shields.io/badge/Practice%20Lab-BE185D?style=for-the-badge)](https://bithappens.dev/learn/?from=github)
[![Study](https://img.shields.io/badge/Study-6D28D9?style=for-the-badge)](https://bithappens.dev/study/?from=github)
[![What's new](https://img.shields.io/badge/What's%20new-0B1026?style=for-the-badge)](https://bithappens.dev/changes/?from=github)

</div>

<img src="./assets/divider.svg" width="100%" alt="" />

### 🎫 About

```yaml
ticket:   BH-0001
priority: P2 (it's always P2 until it's P1)
reporter: every IT tech, every shift
issue: >
  The fix lives in someone's head, a OneNote page,
  or reply #47 of a forum thread.
resolution:
  - write it down once, properly, with sources
  - turn the repetitive parts into tools that run in the browser
  - add a lab so you can practice breaking things safely
status:   in progress  # forever, on purpose
```

**Bit Happens** is a free, no-login IT reference built by a working infrastructure tech. Each guide starts from the symptom: a dead port, a 169.254 address, a bounced email, a failed Intune enrollment. It walks you to the fix with real commands, playbooks and links to the official docs behind every section. No accounts, no cookies, no ads.

<a href="https://bithappens.dev/?from=github"><img src="./assets/numbers.svg" width="100%" alt="By the numbers: 12 guides, 114 browser tools, 115 playbooks, 800+ practice questions, 25 lab tickets, 5 languages" /></a>

### 🧭 Start where it hurts

<table>
<tr>
<td width="33%" valign="top"><a href="https://bithappens.dev/troubleshoot/?from=github"><img src="https://bithappens.dev/og/troubleshoot.jpg" alt="Troubleshoot" /></a><br/><b>Troubleshoot</b><br/><sub>Seven rings from the switch port outward to the fix.</sub></td>
<td width="33%" valign="top"><a href="https://bithappens.dev/tools/?from=github"><img src="https://bithappens.dev/og/tools.jpg" alt="Tools" /></a><br/><b>Tools</b><br/><sub>Paste show output, an error, a config or a packet. Get a plain answer.</sub></td>
<td width="33%" valign="top"><a href="https://bithappens.dev/lab/?from=github"><img src="https://bithappens.dev/og/lab.jpg" alt="Switch Lab" /></a><br/><b>Switch Lab</b><br/><sub>A simulated Cisco IOS XE switch. Fix tickets with real commands.</sub></td>
</tr>
<tr>
<td width="33%" valign="top"><a href="https://bithappens.dev/lab/pc/?from=github"><img src="https://bithappens.dev/og/pclab.jpg" alt="Help Desk Lab" /></a><br/><b>Help Desk Lab</b><br/><sub>A simulated Windows 11 PC: chat with the user, then fix it in PowerShell.</sub></td>
<td width="33%" valign="top"><a href="https://bithappens.dev/journey/?from=github"><img src="https://bithappens.dev/og/journey.jpg" alt="A packet's journey" /></a><br/><b>A packet's journey</b><br/><sub>One HTTPS request, wall jack to server and back, in 12 steps.</sub></td>
<td width="33%" valign="top"><a href="https://bithappens.dev/outages/?from=github"><img src="https://bithappens.dev/og/outages.jpg" alt="Outage replays" /></a><br/><b>Outage replays</b><br/><sub>Meta, CrowdStrike, AWS and more, from their own postmortems.</sub></td>
</tr>
</table>

### 🧪 Ticket of the day

Pick an answer in your head, then click to check it.

<details>
<summary><b>1.</b> A laptop on a desk port shows <code>169.254.23.7</code>. The port light is green and the switch shows it <code>connected</code>. What failed?</summary>
<br/>

**DHCP.** A 169.254.x.x address is APIPA: the PC asked for an address and nobody answered. The cable and port are fine, so check the access VLAN, the gateway's `ip helper-address`, and whether the DHCP scope is full.
→ [Playbook: device has no IP](https://bithappens.dev/networking/playbooks/?from=github#pb-dhcp)

</details>

<details>
<summary><b>2.</b> Someone plugged a small desk switch into a wall jack and the port went dark. <code>show interfaces status</code> says <code>err-disabled</code>. What's the most likely reason?</summary>
<br/>

**BPDU Guard.** The desk switch sent spanning-tree BPDUs into an edge port, so the switch shut the port to prevent a loop. Remove the cause first, then recover the port. Bouncing it with the loop still there just takes it down again.
→ [Playbook: recover an err-disabled port](https://bithappens.dev/networking/playbooks/?from=github#pb-errdis)

</details>

<details>
<summary><b>3.</b> <code>ping 8.8.8.8</code> works, <code>ping google.com</code> fails. Where do you look?</summary>
<br/>

**DNS.** Routing to the internet is fine; name resolution isn't. Check which DNS servers the client got with `ipconfig /all`, then test them with `nslookup google.com <server>`.
→ [Windows: DNS](https://bithappens.dev/networking/end-devices/?from=github#win-dns)

</details>

<sub>Want more? There are 800+ practice questions for A+, Network+, Security+, CCNA, AWS, Azure and Google Cloud in <a href="https://bithappens.dev/study/?from=github">Study mode</a>. The answer shows as soon as you pick.</sub>

### 🛠️ What the guides cover

<a href="https://bithappens.dev/?from=github"><img src="https://skillicons.dev/icons?i=windows,linux,powershell,bash,azure,aws,gcp,docker,kubernetes,terraform,ansible,py,postgres,mysql,githubactions,cloudflare&perline=16" alt="Windows, Linux, PowerShell, Bash, Azure, AWS, Google Cloud, Docker, Kubernetes, Terraform, Ansible, Python, PostgreSQL, MySQL, GitHub Actions, Cloudflare" /></a>

<sub>Plus Cisco IOS XE, Aruba, Palo Alto, Fortinet, Intune, Exchange Online, SIP and Teams Phone, HL7 and medical devices, which don't have icons here.</sub>

**Built with:** <img src="https://skillicons.dev/icons?i=html,css,js,python,nodejs,workers" height="28" alt="HTML, CSS, JavaScript, Python, Node.js, Cloudflare Workers" align="center" /> &nbsp; static pages on Cloudflare, no framework, works offline.

### 🌍 Read it in your language

<div align="center">

<a href="https://bithappens.dev/?from=github"><img src="https://bithappens.dev/flags/us.svg" height="14" alt="" /> English</a> &nbsp;·&nbsp; <a href="https://bithappens.dev/es/?from=github"><img src="https://bithappens.dev/flags/es.svg" height="14" alt="" /> Español</a> &nbsp;·&nbsp; <a href="https://bithappens.dev/fr/?from=github"><img src="https://bithappens.dev/flags/fr.svg" height="14" alt="" /> Français</a> &nbsp;·&nbsp; <a href="https://bithappens.dev/de/?from=github"><img src="https://bithappens.dev/flags/de.svg" height="14" alt="" /> Deutsch</a> &nbsp;·&nbsp; <a href="https://bithappens.dev/ar/?from=github"><img src="https://bithappens.dev/flags/sa.svg" height="14" alt="" /> العربية</a>

</div>

### 📈 Uptime report

<div align="center">

<img src="https://streak-stats.demolab.com?user=jtbithappens&hide_border=true&background=0B1026&stroke=1E1B4B&ring=818CF8&fire=F472B6&currStreakNum=FFFFFF&sideNums=FFFFFF&currStreakLabel=22D3EE&sideLabels=A5B4FC&dates=8B93C9" alt="Contribution streak" height="170" />


<img src="https://raw.githubusercontent.com/jtbithappens/jtbithappens/output/github-contribution-grid-snake-dark.svg" alt="A snake eating the contribution graph" width="100%" />

</div>

<details>
<summary>🥚 <b>Easter eggs</b> (spoilers)</summary>
<br/>

- Type <kbd>↑</kbd> <kbd>↑</kbd> <kbd>↓</kbd> <kbd>↓</kbd> <kbd>←</kbd> <kbd>→</kbd> <kbd>←</kbd> <kbd>→</kbd> <kbd>B</kbd> <kbd>A</kbd> on the home page or any guide for rack mode.
- [Get lost on purpose](https://bithappens.dev/this-page-does-not-exist): the 404 page has a packet-catching game.
- Press <kbd>?</kbd> on the home page or any guide for the keyboard shortcuts.
- Try a bad day: [three tickets on one switch before lunch](https://bithappens.dev/lab/?from=github#bad).

</details>

<br/>

<a href="https://bithappens.dev/?from=github"><img src="./assets/footer.svg" width="100%" alt="Bit happens. Fix it faster. bithappens.dev" /></a>
