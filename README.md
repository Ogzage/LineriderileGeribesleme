from js import robot

<br>`sensor_data = []`<br>
<br>`son_komut = 0`<br>
<br>`while robot.is_ok():`<br>
    
    sensor_data = robot.camera_pixels()
    sayac = 0
    toplam_index = 0
    çizgi_index = 0
    for i in range(0,len(sensor_data)):
        if sensor_data[i] > 50:
            sayac = sayac + 1 
            toplam_index = toplam_index + i
            
    
    
    if sayac > 0:
        çizgi_index = toplam_index / sayac
        error = len(sensor_data) / 2 - çizgi_index
        kp = 20 
        command = error * kp
        robot.move(2.0)
        robot.rotate(command)
        son_komut = command
    else:
        print("çizgi yok")
        robot.move(0.5)
        robot.rotate(son_komut)
