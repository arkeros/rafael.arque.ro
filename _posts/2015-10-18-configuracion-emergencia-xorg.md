---
layout: post
title: Configuración de emergencia para Xorg
author: me
---

Suele pasar que después de una actualización grande tu Linux no arranque debidamente. Puede que se deba a que no se satisfacen algunas dependencias, o que tu configuración de arranque esta buscando algo que no existe. Pero normalmente simple y llanamente te quedas con una bonita pantalla en negro sin poder hacer nada.

Xorg falla al iniciarse. Seguramente tienes instalados los drivers propetarios de nvidia y has actualizado el kernel, entonces lo que te hace falta es volver a instalar los drivers para la nueva versión del kernel. 

Para comprobar que realmente este es el problema, tengo una configuración de emergencia que fuerza a Xorg a utilizar los drivers genericos del sistema:

{% gist 5592dee2265d160b5b73  %}

Para instalarlo ejecuta en tu consola:

{% highlight bash %}
curl https://raw.githubusercontent.com/arkeros/dotfiles/master/etc/X11/xorg.emergency.conf > xorg.emergency.conf
sudo cp xorg.emergency.conf /etc/X11/xorg.conf
sudo reboot
{% endhighlight %}

Si después de reiniciar el sistema arranca correctamente, sabes que unicamente el problema es de los drivers. Vuelve a iniciar en modo seguro y reinstala los drivers adecuados para tu tarjeta. Si no es así ajo y agua y san Google.
