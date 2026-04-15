# CTT's Espanso templates

[Espanso](https://espanso.org/) is a text expander that lets you type a short keyword to instantly insert a full email template. Instead of copying and pasting from a document, you just type a trigger (like `:xfrconf`), and Espanso fills in the rest.

## Setup (one-time)

1. [Install Espanso](https://espanso.org/install/), and follow the prompts.

2. **Clone this repo.** Open the Terminal app (search for "Terminal" in Spotlight), and paste these commands. Then press Enter:

   ```
   mkdir -p ~/code/cttcomedy && cd ~/code/cttcomedy
   git clone https://github.com/cttcomedy/espanso-config.git
   ```

3. **Open Finder**, press **Cmd+Shift+G**, and paste this path:

   ```
   ~/Library/Application Support/espanso/match
   ```

4. **Create a file called `base.yml`** in that folder with the following content (replace `YourFirstName` with your first name):

   ```yaml
   global_vars:
     - name: MyFirstName
       type: echo
       params:
         echo: YourFirstName
   ```

5. **Increase the clipboard threshold.** Open Finder, press **Cmd+Shift+G**, and paste this path:

   ```
   ~/Library/Application Support/espanso/config/
   ```
   
   Open `default.yml` in any text editor, and add this line at the bottom:

   ```yaml
   clipboard_threshold: 10000
   ```

   This tells Espanso to type out templates character by character instead of using the clipboard, which can fail on macOS.

6. **Create a shortcut (symlink) to the shared templates file.** Back in Terminal, paste this command. Then press Enter:

   ```
   ln -s ~/code/cttcomedy/espanso-config/emails.yml ~/Library/Application\ Support/espanso/match/ctt-emails.yml
   ```

   This links the shared templates into your Espanso folder so that you can get updates when you pull in the latest version of the file.

7. **Open Espanso preferences** by clicking the Espanso icon in the menu bar, and make sure it is enabled.

## How to use

1. Open any app where you type emails (Gmail in a browser, etc.).
2. Type a trigger from the table below.
3. A small form will pop up asking you to fill in details (customer name, show date, etc.).
4. Click **Submit** (or press **Enter**), and the full email appears.

## Trigger reference

| Type this | What it does |
|-----------|-------------|
| `:sigctt` | Signature block only |
| `:refpart` | Refund: Partial |
| `:refdeny` | Refund: Denied |
| `:xfrtbd` | Transfer: TBD (date needed) |
| `:xfrconf` | Transfer: Confirmation |
| `:xfrlate` | Transfer: Late request |
| `:xfrfriend` | Transfer: Friend pickup |
| `:pmtfail` | Failed purchase (choose subject line or message body) |
| `:b10pol` | Buy 10 get 1: Policy |
| `:b10conf` | Buy 10 get 1: Confirmation |
| `:special` | Special occasion |
| `:access` | Accessibility needs |
| `:polage` | Policy: Age |
| `:polbags` | Policy: Bags |
| `:polanim` | Policy: Animals |
| `:openmic` | Open mics in the Bay Area |
| `:perffreq` | Performers: Lineup change frequency |

## Troubleshooting

- **Nothing happens when I type a trigger:** Make sure Espanso is enabled. (The menu bar icon should not be greyed out.) If you are typing in a password field or certain secure apps, Espanso may be blocked.
- **Characters get deleted but no template appears:** Make sure you completed step 5 (clipboard threshold) during setup.
- **I don't see the menu bar icon:** Restart Espanso from the Applications folder.

## Updating templates

When the shared `emails.yml` file is updated, pull the latest changes:

```
cd ~/code/cttcomedy/espanso-config
git pull
```

Espanso picks up changes automatically: no restart needed.
