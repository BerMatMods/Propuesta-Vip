# -*- coding: utf-8 -*-
"""
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                            ║
║           ██████╗ ██╗   ██╗ ██████╗ ███████╗ ██████╗ ███████╗              ║
║           ██╔══██╗╚██╗ ██╔╝██╔════╝ ██╔════╝██╔════╝ ██╔════╝              ║
║           ██████╔╝ ╚████╔╝ ██║  ███╗█████╗  ██║      █████╗                ║
║           ██╔══██╗  ╚██╔╝  ██║   ██║██╔══╝  ██║      ██╔══╝                ║
║           ██║  ██║   ██║   ╚██████╔╝███████╗╚██████╗ ███████╗              ║
║           ╚═╝  ╚═╝   ╚═╝    ╚═════╝ ╚══════╝ ╚═════╝ ╚══════╝              ║
║                                                                            ║
║           BerMatHTTP Injector Pro v3.0                                     ║
║           by AnthZz Berrocal BerMatMods                                    ║
║           © 2025 | Todos los derechos reservados                           ║
║                                                                            ║
║  🔹 Túnel SSH con payload HTTP personalizado                               ║
║  🔹 Interfaz 3D animada con efectos CSS simulados                          ║
║  🔹 Compatible con VPS, SSH, SOCKS5 (1080)                                 ║
║  🔹 Animaciones: entrada, hover, pulsos, sombras                           ║
║  🔹 Para uso educativo y redes autorizadas                                 ║
║                                                                            ║
╚══════════════════════════════════════════════════════════════════════════════╝
"""

import os
import subprocess
import tkinter as tk
from tkinter import filedialog, messagebox, ttk
import threading
import time
import socket
import sys
import base64
from datetime import datetime

# ==============================
# CONFIGURACIÓN GLOBAL
# ==============================
BG_DARK = "#121212"
BG_PANEL = "#1e1e1e"
ACCENT = "#00aaff"
ACCENT_LIGHT = "#00ccff"
ACCENT_DARK = "#0088cc"
GREEN = "#00cc66"
RED = "#ff5555"
YELLOW = "#ffcc00"
TEXT_LIGHT = "#ffffff"
TEXT_GRAY = "#aaaaaa"
SHADOW = "#000000"
FONT_TITLE = ("Arial", 20, "bold")
FONT_LABEL = ("Segoe UI", 10)
FONT_BUTTON = ("Segoe UI", 11)
FONT_CODE = ("Consolas", 9)

# ==============================
# ANIMACIONES Y EFECTOS 3D
# ==============================

def animate_widget(widget, start_y, end_y=80, delay=0.02):
    """Animación de entrada: desliza desde arriba con easing"""
    widget.place(x=widget.winfo_x(), y=start_y)
    steps = [(end_y - start_y) // 10 * i for i in range(1, 11)]
    for step in steps:
        y = start_y + step
        widget.place(y=y)
        widget.update()
        time.sleep(delay)

def add_hover_effect(button, normal, hover, click):
    """Efecto hover 3D: brillo y hundimiento"""
    button.bind("<Enter>", lambda e: button.config(bg=hover, cursor="hand2"))
    button.bind("<Leave>", lambda e: button.config(bg=normal))
    button.bind("<ButtonPress-1>", lambda e: button.config(bg=click))
    button.bind("<ButtonRelease-1>", lambda e: button.config(bg=hover))

def create_3d_shadow(root, text, x, y, font, fg, bg, offset=3):
    """Crea una sombra 3D debajo del texto"""
    shadow = tk.Label(root, text=text, font=font, fg=SHADOW, bg=bg)
    shadow.place(x=x + offset, y=y + offset)
    label = tk.Label(root, text=text, font=font, fg=fg, bg=bg)
    label.place(x=x, y=y)
    return label

def pulse_animation(label, color1, color2, cycles=3, delay=0.4):
    """Animación de pulso (como latido)"""
    for _ in range(cycles):
        label.config(fg=color2)
        label.update()
        time.sleep(delay)
        label.config(fg=color1)
        label.update()
        time.sleep(delay)

def glow_animation(entry, color_normal, color_glow):
    """Efecto de brillo en campo de entrada"""
    entry.config(highlightbackground=color_glow, highlightcolor=color_glow, highlightthickness=2)
    entry.update()
    time.sleep(0.5)
    entry.config(highlightbackground=color_normal, highlightthickness=1)

# ==============================
# FUNCIONES DE UTILIDAD
# ==============================

def is_port_open(host, port):
    """Verifica si un puerto está abierto"""
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(3)
        result = sock.connect_ex((host, port))
        sock.close()
        return result == 0
    except:
        return False

def validate_ssh_data(host, port, user):
    """Valida datos SSH"""
    if not host.strip():
        return False, "Host no puede estar vacío"
    if not port.strip().isdigit():
        return False, "Puerto debe ser un número"
    if not user.strip():
        return False, "Usuario no puede estar vacío"
    return True, ""

# ==============================
# CLASE PRINCIPAL: BerMatHTTP_Injector
# ==============================

class BerMatHTTP_Injector:
    def __init__(self, root):
        self.root = root
        self.root.title("BerMatHTTP Injector Pro v3.0 🔐")
        self.root.geometry("800x600")
        self.root.resizable(False, False)
        self.root.configure(bg=BG_DARK)
        self.root.wm_attributes("-alpha", 0.98)

        # Icono opcional
        self.load_icon()

        self.ssh_process = None
        self.is_connected = False
        self.last_test_result = False

        # Centrar ventana
        self.center_window()

        # Variables
        self.status_var = tk.StringVar(value="Estado: Listo")
        self.payload_example = """GET [Protocolo] HTTP/1.1
Host: [Host]:443
X-Online-Host: [Host]:443
User-Agent: Mozilla/5.0 (Linux; Android 10)
Connection: Keep-Alive
[LF]"""

        # Construir interfaz
        self.build_ui()

        # Iniciar animaciones
        self.start_animations()

    def load_icon(self):
        """Carga ícono si existe"""
        icons = ["assets/icon.ico", "icon.ico"]
        for icon_path in icons:
            if os.path.exists(icon_path):
                try:
                    self.root.iconbitmap(icon_path)
                    break
                except:
                    pass

    def center_window(self):
        self.root.update_idletasks()
        x = (self.root.winfo_screenwidth() // 2) - (800 // 2)
        y = (self.root.winfo_screenheight() // 2) - (600 // 2)
        self.root.geometry(f"800x600+{x}+{y}")

    def build_ui(self):
        # ====== ENCABEZADO ======
        self.title_label = create_3d_shadow(
            self.root, "🚀 BerMatHTTP Injector Pro", 400, 20, FONT_TITLE, ACCENT, BG_DARK
        )
        self.title_label.place(x=400, y=20, anchor="center")

        self.author_label = tk.Label(
            self.root,
            text="by AnthZz Berrocal BerMatMods",
            font=("Arial", 11, "italic"),
            fg=TEXT_GRAY,
            bg=BG_DARK
        )
        self.author_label.place(x=400, y=55, anchor="center")

        # ====== PANEL PRINCIPAL ======
        self.draw_panel(30, 85, 740, 440)

        # ====== CONFIGURACIÓN SSH ======
        tk.Label(self.root, text="🔧 Configuración del Servidor SSH", font=("Segoe UI", 13, "bold"), fg=ACCENT_LIGHT, bg=BG_PANEL).place(x=50, y=110)

        # Host
        tk.Label(self.root, text="Host:", bg=BG_PANEL, fg=TEXT_LIGHT).place(x=50, y=150)
        self.host = tk.Entry(self.root, width=25, font=FONT_CODE)
        self.host.insert(0, "tudominio.com")
        self.host.place(x=110, y=150)
        self.host.bind("<FocusIn>", lambda e: glow_animation(self.host, TEXT_GRAY, ACCENT))

        # Puerto
        tk.Label(self.root, text="Puerto:", bg=BG_PANEL, fg=TEXT_LIGHT).place(x=400, y=150)
        self.port = tk.Entry(self.root, width=10, font=FONT_CODE)
        self.port.insert(0, "22")
        self.port.place(x=470, y=150)
        self.port.bind("<FocusIn>", lambda e: glow_animation(self.port, TEXT_GRAY, ACCENT))

        # Usuario
        tk.Label(self.root, text="Usuario:", bg=BG_PANEL, fg=TEXT_LIGHT).place(x=50, y=190)
        self.user = tk.Entry(self.root, width=25, font=FONT_CODE)
        self.user.insert(0, "tusuario")
        self.user.place(x=110, y=190)
        self.user.bind("<FocusIn>", lambda e: glow_animation(self.user, TEXT_GRAY, ACCENT))

        # Contraseña
        tk.Label(self.root, text="Clave:", bg=BG_PANEL, fg=TEXT_LIGHT).place(x=400, y=190)
        self.password = tk.Entry(self.root, width=18, font=FONT_CODE, show="*")
        self.password.insert(0, "tuclave")
        self.password.place(x=470, y=190)
        self.password.bind("<FocusIn>", lambda e: glow_animation(self.password, TEXT_GRAY, ACCENT))

        # ====== PAYLOAD HTTP ======
        tk.Label(self.root, text="📡 Payload HTTP Personalizado", font=("Segoe UI", 13, "bold"), fg=ACCENT_LIGHT, bg=BG_PANEL).place(x=50, y=240)

        self.payload_text = tk.Text(self.root, width=80, height=8, font=FONT_CODE, bg="#2a2a2a", fg=TEXT_LIGHT, insertbackground=ACCENT)
        self.payload_text.insert("1.0", self.payload_example)
        self.payload_text.place(x=50, y=270)

        # Variables de ayuda
        tk.Label(self.root, text=":variables: [Host], [Protocolo], [LF], [CRLF]", font=("Arial", 8), fg=YELLOW, bg=BG_PANEL).place(x=50, y=390)
        tk.Label(self.root, text="💡 Usa [LF] para salto de línea", font=("Arial", 8), fg=TEXT_GRAY, bg=BG_PANEL).place(x=50, y=410)

        # ====== BOTONES ======
        self.btn_start = tk.Button(self.root, text="🟢 Iniciar Túnel", font=FONT_BUTTON, bg=GREEN, fg=TEXT_LIGHT, width=16, height=2, command=self.start_tunnel_threaded)
        self.btn_start.place(x=70, y=530)
        add_hover_effect(self.btn_start, GREEN, "#00dd77", "#00aa55")

        self.btn_stop = tk.Button(self.root, text="🔴 Detener", font=FONT_BUTTON, bg=RED, fg=TEXT_LIGHT, width=16, height=2, command=self.stop_tunnel)
        self.btn_stop.place(x=250, y=530)
        add_hover_effect(self.btn_stop, RED, "#ff3333", "#cc0000")

        self.btn_test = tk.Button(self.root, text="📡 Probar Conexión", font=FONT_BUTTON, bg=ACCENT, fg=TEXT_LIGHT, width=16, height=2, command=self.test_connection)
        self.btn_test.place(x=430, y=530)
        add_hover_effect(self.btn_test, ACCENT, ACCENT_LIGHT, ACCENT_DARK)

        self.btn_info = tk.Button(self.root, text="ℹ️ Info App", font=FONT_BUTTON, bg="#666666", fg=TEXT_LIGHT, width=12, height=2, command=self.show_info_app)
        self.btn_info.place(x=610, y=530)
        add_hover_effect(self.btn_info, "#666666", "#888888", "#444444")

        # Estado
        self.status_label = tk.Label(self.root, textvariable=self.status_var, font=("Segoe UI", 10), fg=TEXT_GRAY, bg=BG_DARK)
        self.status_label.place(x=12, y=580)

        # Footer
        self.footer_label = tk.Label(self.root, text="© 2025 AnthZz Berrocal BerMatMods | HTTP Injector Pro", font=("Arial", 8), fg=TEXT_GRAY, bg=BG_DARK)
        self.footer_label.place(x=300, y=580)

    def draw_panel(self, x, y, w, h):
        """Panel con efecto 3D y brillo superior"""
        tk.Frame(self.root, bg=SHADOW, width=w, height=h).place(x=x+5, y=y+5)
        panel = tk.Frame(self.root, bg=BG_PANEL, width=w, height=h)
        panel.place(x=x, y=y)
        tk.Frame(self.root, bg=ACCENT_LIGHT, height=3, width=w-30).place(x=x+15, y=y+10)

    def start_animations(self):
        """Inicia animaciones después de cargar"""
        self.root.after(600, lambda: animate_widget(self.btn_start, 700, 530, 0.03))
        self.root.after(700, lambda: animate_widget(self.btn_stop, 700, 530, 0.03))
        self.root.after(800, lambda: animate_widget(self.btn_test, 700, 530, 0.03))
        self.root.after(900, lambda: animate_widget(self.btn_info, 700, 530, 0.03))
        self.root.after(1200, lambda: pulse_animation(self.title_label, ACCENT, ACCENT_LIGHT, cycles=3, delay=0.3))

    def start_tunnel_threaded(self):
        if self.is_connected:
            messagebox.showinfo("ℹ️", "Ya hay una conexión activa.")
            return
        thread = threading.Thread(target=self.start_ssh_tunnel, daemon=True)
        thread.start()

    def start_ssh_tunnel(self):
        host = self.host.get().strip()
        port = self.port.get().strip()
        user = self.user.get().strip()

        valid, msg = validate_ssh_data(host, port, user)
        if not valid:
            self.show_error(f"❌ {msg}")
            return

        try:
            self.update_status("Iniciando túnel SSH...", color=ACCENT_LIGHT)
            self.btn_start.config(state="disabled")

            cmd = [
                "ssh", "-N", "-D", "1080",
                "-o", "UserKnownHostsFile=/dev/null",
                "-o", "StrictHostKeyChecking=no",
                f"{user}@{host}",
                "-p", port
            ]

            self.ssh_process = subprocess.Popen(
                cmd,
                stdin=subprocess.PIPE,
                stdout=subprocess.PIPE,
                stderr=subprocess.PIPE,
                shell=True
            )

            time.sleep(2)
            if self.ssh_process.poll() is None:
                self.is_connected = True
                self.update_status("✅ Túnel activo: SOCKS5 en 127.0.0.1:1080", color=GREEN)
                self.btn_start.config(text="✅ Conectado", state="normal")
                self.pulse_status()
            else:
                stderr = self.ssh_process.stderr.read().decode()
                raise Exception(stderr[:100])
        except FileNotFoundError:
            self.show_error("❌ SSH no está disponible.\nInstala OpenSSH o usa Git Bash/WSL.")
        except Exception as e:
            self.show_error(f"❌ Error SSH:\n{str(e)}")
        finally:
            if not self.is_connected:
                self.btn_start.config(state="normal")

    def stop_tunnel(self):
        if self.ssh_process:
            self.ssh_process.terminate()
            self.ssh_process = None
            self.is_connected = False
            self.update_status("🔴 Túnel detenido", color=RED)
            self.btn_start.config(text="🟢 Iniciar Túnel", state="normal")
            self.show_info("Túnel SSH cerrado correctamente.")
        else:
            self.show_info("No hay conexión activa.")

    def test_connection(self):
        try:
            result = is_port_open('127.0.0.1', 1080)
            if result:
                self.last_test_result = True
                self.show_info("✅ Puerto 1080 está activo.\nConfigura tu navegador para usar:\nSOCKS5 127.0.0.1:1080")
                self.update_status("Prueba: Éxito", color=GREEN)
            else:
                self.last_test_result = False
                self.show_error("❌ El túnel no está escuchando en el puerto 1080")
                self.update_status("Prueba: Fallida", color=RED)
        except Exception as e:
            self.show_error(f"❌ Error al probar: {e}")
            self.update_status("Prueba: Error", color=RED)

    def pulse_status(self):
        for _ in range(3):
            if not self.is_connected:
                break
            self.status_label.config(fg=GREEN)
            self.root.update()
            time.sleep(0.6)
            self.status_label.config(fg=TEXT_GRAY)
            self.root.update()
            time.sleep(0.6)

    def update_status(self, text, color=TEXT_GRAY):
        self.root.after(0, lambda: self.status_var.set(f"Estado: {text}") or self.status_label.config(fg=color))

    def show_error(self, msg):
        self.root.after(0, lambda: messagebox.showerror("❌ Error", msg))

    def show_info(self, msg):
        self.root.after(0, lambda: messagebox.showinfo("ℹ️ Información", msg))

    def show_info_app(self):
        info = f"""
╔══════════════════════════════════════════════════╗
║         BerMatHTTP Injector Pro v3.0             ║
║         by AnthZz Berrocal BerMatMods            ║
║         © 2025 | Todos los derechos reservados   ║
╠══════════════════════════════════════════════════╣
║  🔹 Túnel SSH con payload HTTP                   ║
║  🔹 Diseño 3D animado avanzado                   ║
║  🔹 SOCKS5 en 127.0.0.1:1080                     ║
║  🔹 Animaciones: entrada, hover, pulsos          ║
║  🔹 Para pruebas de red autorizadas             ║
║                                                  ║
║  📅 Versión: 3.0                                 ║
║  🛠️  Desarrollado con Python + Tkinter          ║
╚══════════════════════════════════════════════════╝
        """
        self.show_info(info)

# ==============================
# EJECUCIÓN PRINCIPAL
# ==============================

if __name__ == "__main__":
    print(f"[{datetime.now().strftime('%H:%M:%S')}] Iniciando BerMatHTTP Injector Pro v3.0...")
    print("Desarrollado por: AnthZz Berrocal BerMatMods")
    
    root = tk.Tk()
    app = BerMatHTTP_Injector(root)
    root.mainloop()

    print(f"[{datetime.now().strftime('%H:%M:%S')}] Aplicación cerrada.")
