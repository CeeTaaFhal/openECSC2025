# 🟡 Yellow Submarine Challenge  
### *CTF Write-up*

---

## 🧩 Challenge
We are given an image file named **`yellow.png`**. The goal is to extract a hidden flag from it.

---

## ⚙️ Single-file Steps (beginner-friendly)

> Copy and run the commands exactly as shown. Each command has a one-line plain-English note.

```bash
# 1) See what type of file it is
file yellow.png
# -> tells you "PNG image" or other file type

# 2) Show readable text inside the file (scan output with arrow keys and q to quit)
strings yellow.png | less
# -> lists all readable words inside the binary file

# 3) Show only lines that mention "IDAT" (PNG data chunks)
strings yellow.png | grep IDAT
# -> narrows output to lines containing the chunk name "IDAT"

# 4) Extract the first character of each "IDAT" line and join them to reveal the hidden text
strings yellow.png | grep IDAT | cut -c1 | tr -d '\n' 
# -> prints one continuous string; this is where the flag appears for this challenge
