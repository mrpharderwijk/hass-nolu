1. Install [Samba Share](https://github.com/home-assistant/addons/blob/master/samba/DOCS.md) (You'll need this to place the Nolu files on your Home Assistant server)
      1. Enable the toggles (Start on boot, Watchdog, Auto update) 
      2. Go over to the configuration tab of the Samba Share add-on and fill in the username and password and hit save
      3. Head back to the info tab of the Samba Share add-on and press start
   2. Install the Visual Studio Code add-on (or File Explorer)
      1. Tick all the toggles and start the add-on
   3. Install the SSH & Web Terminal add-on (Home Assistant Community Add-on)
      1. Enable all the toggles
      2. Go over to the configuration tab of the SSH & Web Terminal add-on and fill in the username and password and hit save
      3. start the add-on
   4. Install [HACS](https://hacs.xyz/docs/installation/installation/) (!important! Make sure you have a Github account. If you don't have one yet create it prior to this step!)
      1. Just to be sure: Restart your Home Assistant by going to configuration > Server Controls > Check Configuration (if OK, proceed to restart, otherwise check FAQ) > Restart
      2. Clear your browser cache, while your Home Assistant is restarting
      3. If Home Assistant is restarted you might need to login again due to the cache clearing, so do that now
      4. Go to configuration > Add integration > search for `hacs` > click it
      5. Go through all the steps of the installation process
   5. Now we need to install some HACS integrations
      1. Install [browser_mod](https://github.com/thomasloven/hass-browser_mod)
         1. Download the zip and unpack it or Clone the repo locally
         2. Inside the custom_components there is a folder browser_mode, move it to your Hass `custom_components` -folder
      2. Install [lovelace_gen](https://github.com/thomasloven/hass-lovelace_gen)
         1. Download the zip and unpack it or Clone the repo locally
         2. Inside the custom_components there is a folder lovelace_gen, move it to your Hass `custom_components` -folder
      3. Install [card-mod](https://github.com/thomasloven/lovelace-card-mod)
         1. Click `Explore & Add repositories` and search for card-mod
         2. Click on the search result
         3. Click `Install this repository in HACS`
      4. Just to be sure: Restart your Home Assistant by going to configuration > Server Controls  > Check Configuration (if OK, proceed to restart, otherwise check FAQ) > Restart
      5. Your not done yet! Now we need to activate each integration!
      6. Go to HACS > Integrations tab > Explore & Add repositories > Search for browser_mod > click the search result > Install the repository in HACS
         1. Click Explore & Add repositories 
         2. Search for and install each integration in the HACS integrations list (see below)
      7. Go to the Frontend tab
         1. Search for and install each frontend repository in the HACS frontend list (see below)
   6. Just to be sure: Restart your Home Assistant by going to configuration > Server Controls > Check Configuration (if OK, proceed to restart, otherwise check FAQ) > Restart

   ----
