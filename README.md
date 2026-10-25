# Port Dojo — learn network ports through pictures and practice

Port Dojo is a cat-themed network-port learning game that combines visual memory stories, typed recall, and spaced repetition.

I created this project while studying IT because memorizing a list of numbers was not enough. I wanted each number to connect to a scene I could picture, then practice recalling the service and port without looking.

**[Play Port Dojo](https://erivera3.github.io/port-dojo/)** · [Download the single HTML file](https://github.com/erivera3/port-dojo/raw/refs/heads/main/index.html)

The complete game is packaged in **index.html**, including both illustrated memory maps, styles, and JavaScript. Open it in a browser or play on GitHub Pages; no installation or build is required.

## The idea: turn a port number into a memory story

Instead of repeatedly reading “FTP: 20/21,” picture a **file-transfer club**. You need to be **21 to enter**. That gives you a hook for FTP port 21; pair it with neighboring port 20 for active-mode data transfer.

For **SMTP 25**, picture a cat saying, **“I need to send out 25 emails.”** The action connects SMTP to sending mail, and the number connects it to port 25.

These are mnemonic associations: simple, exaggerated stories that help bring a fact back to mind. The scene is a cue; the technical explanation gives it meaning.

## Memory map

| Service | Port(s) | Picture or memory story | What to remember |
| --- | --- | --- | --- |
| FTP | 20 / 21 | The file-transfer club: you must be 21 to enter; pair it with 20. | 21 controls the session; 20 is the traditional server data port for active-mode FTP. |
| SSH | 22 | Two locks on two doors: 2–2. | Secure remote shell access. |
| Telnet | 23 | 23 people talking on an unsecured telephone. | Remote terminal access without built-in encryption. |
| SMTP | 25 | “I need to send out 25 emails.” | Mail transfer between servers. |
| DNS | 53 | 53 detectives finding website addresses. | Resolving names and other DNS records. |
| DHCP | 67 / 68 | 67 hands out addresses; 68 receives them. | 67 is the server; 68 is the client. |
| HTTP | 80 | An 80-year-old browsing the web. | Unencrypted web traffic. |
| POP3 | 110 | 110 letters popping out of a mailbox. | Retrieving email; whether copies stay on the server depends on client settings. |
| IMAP | 143 | 143 emails staying in the mailbox. | Accessing and synchronizing server-side mailboxes. |
| HTTPS | 443 | 443 locks protecting a website. | Encrypted web traffic. |
| SMB / CIFS | 445 | 445 shared folders. | Network file and printer sharing. |
| RDP | 3389 | 3389 is the door code to a remote desktop. | Remote desktop access. |
| NetBIOS / NetBT | 137 / 138 / 139 | Three neighboring doors: names, messages, sessions. | 137: name service; 138: datagrams; 139: sessions. |
| LDAP | 389 | A cat librarian looks up a record in directory drawer 389. | Accessing and managing directory information. |

The game covers **14 protocol families, 18 individual port facts, and 36 cards**, with each fact practiced in both directions. It focuses on service names, port numbers, and their purposes.

The study list follows the ports explicitly listed in **CompTIA A+ Core 1 220-1201, objective 2.1**. It is an independent study aid, not a complete exam-preparation course. Real configurations can use other ports; the memory stories describe common study mappings.

## How to play

1. **Start in Picture dojo.** Explore the illustrated poster. Click a scene to see its memory story and a short explanation of the service.
2. **Study a few scenes.** Say the service, port, and purpose aloud. For example: “SMTP, 25, sends mail between servers.”
3. **Hide the picture and practice.** Type the port when shown a service, or type the service when shown a port.
4. **Check the answer.** The matching illustration returns after the answer is revealed, connecting the fact back to its scene.
5. **Rate your recall.** Choose Again, Hard, Good, or Easy. You choose every rating yourself, including when your wording differs from the revealed answer. The game does not mark typed answers right or wrong or force a rating.
6. **Keep practicing in Cram session**, or switch to Spaced review to return for scheduled cards.

Choose one protocol family or practice them all. Select service → port, port → service, or both.

For services with multiple roles, include the role in reverse answers. For example, port 67 requires **DHCP server**, while 68 requires **DHCP client**. FTP control/data and NetBIOS roles are also distinct.

**Cram session is the default:** every filtered card is available immediately, with no daily cap, timer, or session cutoff. Again and Hard return cards sooner; Good and Easy return them later in the same session. Gaps are up to 2, 4, 8, and 16 other cards respectively, shortened for small decks. These are practical defaults, not scientifically optimized intervals. Cram ratings do not change saved spaced-review progress. The session queue resets when filters change or the page reloads.

**Free practice** shuffles cards for extra attempts without changing the review schedule. **Spaced review** retains time-based scheduling for longer-term practice.

## How to learn from it

**Picture it → say it → hide it → recall it → check it → revisit it.**

Use two or three scenes at a time. Form a clear mental image, connect the number to the service, then look away and produce the answer yourself. Looking at a familiar picture is easier than recalling a fact without help.

Practice both directions. Knowing “SSH uses 22” and recognizing “22 means SSH” are separate recall tasks.

When you miss a card, revisit its scene, explain the service in your own words, and try again. Use an association that makes sense to you if the supplied one does not stick.

The three learning techniques work together:

- **Visual mnemonics:** give an abstract number a memorable picture or story.
- **Active recall:** require you to produce the answer before seeing it.
- **Spaced repetition:** revisit the fact across time rather than only repeating it in one sitting.

The illustrations support recall; they do not guarantee retention.

## Spaced repetition and progress

The game uses a **simplified SM-2-inspired scheduler with Anki-style ratings**. It is not Anki and does not use Anki’s FSRS algorithm.

| Rating | Meaning | New-card behavior |
| --- | --- | --- |
| Again | I forgot or answered incorrectly. | Return after 1 minute. |
| Hard | I recalled it with effort. | Return after 6 minutes. |
| Good | I recalled it correctly. | Return after 10 minutes; a subsequent Good graduates to a 1-day review. |
| Easy | I recalled it immediately. | Graduate to a 4-day review. |

Established review intervals grow according to the rating and the card’s ease factor. Forgotten review cards return to short relearning steps. Each direction has its own schedule.

In Spaced review, due cards come first and all new cards are available without a daily cap. Scheduled intervals apply only to Spaced review; Cram session lets you continue immediately.

Progress is stored in the same browser and device. The Progress screen supports JSON backup export and import. Export before clearing browser data or moving devices. There is no account or cross-device sync, and backups are not Anki deck files.

## My role and the implementation

I supplied the learning goal, visual reference, memory-technique requirements, and direction for the study flow. The code, supporting illustrations, content organization, and checks were developed with AI assistance.

The downloadable game is one self-contained HTML file with embedded CSS, JavaScript, both illustrations, and browser storage. Its design centers on the supplied illustrated cat poster, with additional NetBIOS and LDAP scenes.

The source implementation was checked for scheduling, learning and relearning steps, card counts, port coverage, and unlimited cram queue cycling, including one-card decks. The bundled HTML was checked for JavaScript syntax and browser operation. Ratings are self-assessed. This is a personal IT learning project.

## Run or host it yourself

Download `index.html` and open it in a browser. To host on GitHub Pages, place it at the repository root and select **Settings → Pages → Deploy from a branch → main → / (root)**. There are no separate asset files or build dependencies. Browser progress is specific to the browser and origin; export a backup before moving between the hosted game and a downloaded copy.

## References

- [CompTIA A+ 220-1201 objectives](https://lecbyo.files.cmp.optimizely.com/download/34be017cb73211ef8985a6f347fbf652) — objective 2.1.
- [IANA service names and port numbers](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml).
- [Anki: rating answers](https://docs.ankiweb.net/studying.html).
- [Anki scheduling algorithms](https://faqs.ankiweb.net/what-spaced-repetition-algorithm.html).
- [Dunlosky et al. (2013)](https://doi.org/10.1177/1529100612453266) — review of learning techniques, including practice testing and distributed practice.
