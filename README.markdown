# Stuff
This is my repository for some stuffs, about configurations or hack some plugins
for me.

### .autotest
Rewrite show message method (growl), because in Ubuntu is set default delay to 8
seconds with notify-send(use notifyOSD), what slowdown deploy.

aosd_cat package is requested in Linux.

    def self.growl(title, message, icon, priority=0, stick="")
    growl = File.join(GEM_PATH, 'growl', 'growlnotify')
    image = File.join(@@image_dir, "#{icon}.png")
    #system %(notify-send "#{title}" "#{message}" -i #{image} -t 1)
    options = "-u 800 -o 100 -n 28 -p 7 -x 0 -y -50 -B black -r 155 -b 155 -d 30 -l 3 -a 3"
    if message =~ /fail/
      options += " -R red"
      title = "FAIL"
    elsif message =~ /examples/
      options += " -R green"
      title = "PASS"
    end
      system %( echo "#{title} - #{message}" | aosd_cat #{options} )
    end

