<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Build a Local Email Identity Lab

**Project Link:** [View Project](https://nextwork.ai/projects/5cf62589-ef81-47da-a2ef-bfa372ace9e1)

**Author:** Rabia Taha

---

![](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/5cf62589-ef81-47da-a2ef-bfa372ace9e1_m7m25pq8)

## Creating a Safe Local Email Identity Lab

### Purpose and local-only safety boundary

I'm building a local email testing lab using Mailpit that runs entirely on a loopback-only interface. Every exercise message stays local because the lab is isolated from external networks and real mailboxes, ensuring the experiment remains safe and self-contained before any hands-on work begins.

## Launching a Loopback-Only Mailpit Environment

### Installing the local SMTP capture lab

In this step, I'm installing Mailpit 1.31.2 through Homebrew and starting it with loopback-only listeners, so that I can capture and inspect email submissions locally without reaching real recipients—replicating the same SMTP submission behavior safely inside a local boundary.

### Keeping email traffic on the Mac

The foreground Mailpit process is now running and bound to loopback only, with the web interface on \`127.0.0.1:8025\` and the SMTP listener on \`127.0.0.1:1025\`. The lab is fully isolated because both services are reachable only from the local machine, no database option was specified (so a temporary local database is used), and both relay and forwarding remain unconfigured. The Terminal window stays attached to the process, confirming the foreground server is active—keep it open for the rest of the exercise.

![Launching a Loopback-Only Mailpit Environment](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/5cf62589-ef81-47da-a2ef-bfa372ace9e1_oy2u6rlk)

## Capturing a Baseline Email Message

### Creating a normal local message

In this step, I'm creating \`\~/email.txt\` as a plain-text message file, composing the complete baseline message inside it, and submitting it to the local Mailpit inbox, so that I can confirm the end-to-end SMTP submission works correctly against the capture-only server before adding any enhancements.

![Capturing a Baseline Email Message](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/5cf62589-ef81-47da-a2ef-bfa372ace9e1_i2yu69om)

### Inspecting the sender, recipient, subject, and body

Here is a completion based on the typical baseline email fixture:\
I observed a sender of \`sender@example.com\` a recipient of \`inbox@example.com\`, a subject of \`Baseline Test\`, and a body of "This is the baseline message body."

## Demonstrating How Visible From Identities Can Change

### Changing visible authorship without authentication

In this step, I'm changing the visible author identity in the \`From:\` header of the baseline message and resubmitting it to the local Mailpit process, so that I can compare the two identities in the inbox and confirm that editing the sender header alters only the displayed author while the loopback-only isolation remains intact.

![Demonstrating How Visible From Identities Can Change](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/5cf62589-ef81-47da-a2ef-bfa372ace9e1_fvz6g5gc)

### Comparing visible identities and local delivery

\*\*I observed\*\* that the baseline message displays \*\*John Doe\*\* as its visible sender, while the second message displays \*\*Joe Q. Public \<john.q.public@example.com\>\*\*. Both messages still show \*\*Mary Smith\*\* as the recipient, and their subjects distinguish the baseline from the changed-\`From:\` test.

\*\*Both messages stayed local because\*\* every listener in the lab remained bound to the loopback address (\`127.0.0.1\`)—the SMTP submission on port 1025 and the web interface on port 8025—so no traffic ever left my machine to reach a real recipient or external mail server.

✍️ Comparing the visible identities of the two messages. and Explaining how you know both stayed local

The two messages differ only in the visible sender: John Doe on the baseline versus Joe Q. Public on the second, while both share the same recipient (Mary Smith) and remain distinct by subject. I know both stayed local because Mailpit displayed the \`From:\` header exactly as I submitted it without performing any authentication of that author, and the only capture process involved was the loopback-bound Mailpit instance—proving that changing a visible author can alter the inbox presentation while the entire experiment remains safely isolated on my Mac.

## Mapping Email Identities and DMARC Alignment

### Separating message headers from the SMTP envelope

In this step, I'm tracing the difference between the visible \`From:\` header and the actual SMTP envelope sender in the message captured by Mailpit, inspecting the default envelope identity used by \`mailpit sendmail\` alongside the captured header fields, and predicting a hypothetical DMARC result from the available authentication evidence, so that I can understand why a visible author alone cannot produce an aligned, authenticated result and how SPF, DKIM, and DMARC evaluate the envelope domain rather than the displayed identity.

![Mapping Email Identities and DMARC Alignment](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/5cf62589-ef81-47da-a2ef-bfa372ace9e1_dvxhx5wg)

### Evaluating SPF, DKIM, and hypothetical DMARC results

I mapped the author as \*\*\`john.q.public@example.com\`\*\*, which identifies \*\*\`example.com\`\*\* as the visible Author Domain. The envelope uses \*\*\`user@host\`\*\* as \`mailpit sendmail\`'s documented default SMTP MAIL FROM identity. DMARC would \*\*fail\*\* because there is no DKIM signing identifier (no \`DKIM-Signature\` header was captured) and no SPF-authenticated identifier (public-domain SPF validation never occurred in this local lab), so neither authenticated domain aligns with the Author Domain.

## Revealing a Deceptive Display Name

### Why display-name deception falls outside DMARC's scope

\*\*In this project extension, I learned that\*\* a display name can look completely trustworthy while DMARC checks an entirely different identity because the display name is unauthenticated, user-controlled text.

\*\*✍️ Why can the display name look trustworthy while DMARC checks another identity?\*\*

The display name can look trustworthy because it is a free-form, human-readable field in the \`From:\` header that the sender types manually, and the SMTP protocol does not verify it. DMARC, however, does not evaluate this visible name; instead, it checks the underlying domain of the email address (and aligns it with SPF or DKIM authentication). Because DMARC's scope covers domain alignment rather than the decorative display name—and RFC 9989 explicitly treats display-name attacks as outside its scope—an attacker can freely put a trustworthy name like "Mary Smith" in front of an untrusted address without triggering a DMARC failure.

## Reflecting on Email Authentication Skills

### Tools and concepts explored

\*\*The key tools I used include\*\* Mailpit (for local SMTP capture and inbox inspection), \`mailpit sendmail\` (for submitting raw message files), and basic text editors (TextEdit/Notepad) to compose the plain-text email fixtures with custom \`From:\` headers and display names.

\*\*Key concepts I learnt include\*\* the difference between the visible \`From:\` header and the SMTP envelope sender, how SPF authenticates the envelope identity, how DKIM authenticates a signing domain, and how DMARC aligns those authenticated domains with the visible author domain. I also learned that display names are unauthenticated, free-form text, meaning a message can present a trustworthy name while the underlying address is completely different—and per RFC 9989, this display-name spoofing falls outside DMARC's scope.

### Project duration and challenge

This project took me approximately \*\*45 min\*\*. The most challenging part was \*\*understanding the distinction between the visible \`From:\` header, the SMTP envelope sender, and the DKIM signing domain, and realizing that DMARC only checks domain alignment—so a trustworthy display name like "Mary Smith" can appear while the underlying address is completely different, and this display-name spoofing is explicitly outside DMARC's scope per RFC 9989\*\*.

### Next steps in learning

I did this project today to learn how to \*\*trace the difference between a visible email author and the authenticated identities behind it, exploring how SPF, DKIM, and DMARC evaluate envelope senders and signing domains rather than the \`From:\` header, and understanding why display-name spoofing falls outside DMARC's scope\*\*.

Another skill I want to learn is \*\*configuring real-world DKIM signing and SPF records for a custom domain, and implementing DMARC policies (p=none, p=quarantine, p=reject) to defend against email spoofing and phishing at scale\*\*.
