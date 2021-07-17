Tentacle Manager
================

OctBot is fully modular, so you can install any modules you want !

[![tentacles](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tentacles.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tentacles.jpg)

You can find in
[this](https://github.com/Drakkar-Software/OctoBot-Tentacles) repository
all default tentacles (modules) you can create to custom your own
cryptocurrencies trader bot.

**It\'s very simple !** If you used [the OctoBot
binary](https://github.com/Drakkar-Software/OctoBot-Binary/releases) to
install OctoBot, you dont need to do this.

Otherwise, after the [developer installation](For-Developers.html) of
your OctoBot, you just have to type :

``` bash
python start.py tentacles --install --all
```

And all the default tentacles package from this repository will be
installed (and activated).

If you want to modify or disable some of them [see this
page](Customize-your-OctoBot.html).

Add new tentacles packages to your OctoBot
------------------------------------------

### Using the web interface

[![tentacles\_packages](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tentacles_packages.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tentacles_packages.jpg)

Got to the **Tentacles** section on the navigation bar, then go to
**INSTALL TENTACLES PACKAGES** and register the address (local or url)
of the wanted tentacles packages. This will automatically install the
package in your OctoBot.

Install a specific tentacle
---------------------------

*This tentacle have to be available in one of your tentacles
repositories (see above).*

To install a tentacle, type:

``` bash
python start.py tentacles --install NAME_OF_YOUR_TENTACLE
```
