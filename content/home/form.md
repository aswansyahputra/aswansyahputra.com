+++
# Custom widget.
# An example of using the custom widget to create your own homepage section.
# To create more sections, duplicate this file and edit the values below as desired.
widget = "custom"
active = false
date = "2016-04-20T00:00:00"

# Note: a full width section format can be enabled by commenting out the `title` and `subtitle` with a `#`.
title = "Hubungi saya"
subtitle = ""

# Order that this section will appear in.
weight = 70

+++

<div class="container">
	<form name="Kontak" method="POST" netlify>
          <label for="nama">Nama: </label><br>
          <input type="text" name="nama" required><br>
          <label for="surel">Surel: </label><br>
          <input type="email" name="surel" required><br>
          <label for="pesan">Pesan: </label><br>
          <textarea rows="5" name="pesan" placeholder="Silakan tulis pesan Anda disini"></textarea><br>
	  <div netlify-recaptcha></div><br>
          <button type="submit">Kirim</button>
        </form>
</div>

