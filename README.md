# MICRO-IT-Qr-CODE-GENimport qrcode
import tkinter as tk
from tkinter import messagebox, filedialog

def generate_qr():
    data = entry.get()
    if not data.strip():
        messagebox.showerror("Error", "Please enter some text or URL")
        return

    qr = qrcode.QRCode(
        version=1,
        error_correction=qrcode.constants.ERROR_CORRECT_H,
        box_size=10,
        border=4,
    )
    qr.add_data(data)
    qr.make(fit=True)

    img = qr.make_image(fill_color="black", back_color="white")

    save_path = filedialog.asksaveasfilename(defaultextension=".png",
                                             filetypes=[("PNG files", "*.png")])
    if save_path:
        img.save(save_path)
        messagebox.showinfo("Success", f"QR code saved to:\n{save_path}")

# GUI Setup
root = tk.Tk()
root.title("QR Code Generator")

tk.Label(root, text="Enter text or URL:").pack(pady=10)
entry = tk.Entry(root, width=40)
entry.pack(padx=20)

tk.Button(root, text="Generate QR Code", command=generate_qr).pack(pady=20)

root.mainloop()ERATOR-
