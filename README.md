with open('bin/path_LD.txt', 'r', encoding='utf-8') as file:
    LDpane = file.readline().strip()  #path_ldplayer ที่อยู่ไฟล์ Ldplayer


#คำสั่งเรียกดูชื่อ Ldplayer ที่มีอยู่ในlist
ldplayer_path = f'{LDpane}'
base_command = r'ldconsole list'
ldplayer_command = f'{ldplayer_path}\{base_command}'
completed_process = subprocess.run(ldplayer_command, shell=True, capture_output=True, text=True)


#คำสั่งเปิดหน้าจอ Ldplayer
Runld = subprocess.run(f'{ldplayer_path}\dnconsole.exe launch --name {ldplayer_name}', shell=True)

#คำสั่งเรียงหน้าจอ Ldplayer
sortWnd_command = r'ldconsole sortWnd'
ldplayer_commandsortWnd = f'{LDpane}\{sortWnd_command}'
completed_process = subprocess.run(ldplayer_commandsortWnd, shell=True, capture_output=True, text=True)


# ปิดหน้าต่าง Ldplayer ทั้้งหมด
ldplayer_path = f'{LDpane}'
ExitAll_ldplayer = subprocess.run(f'{ldplayer_path}\ldconsole.exe quitall', shell=True) 



adb_path = "bin/adb.exe"
kill_server = subprocess.run([adb_path, 'kill-server'], capture_output=True, text=True)
print(kill_server)


devices = subprocess.run([adb_path, 'devices'], capture_output=True, text=True)
print(devices)
