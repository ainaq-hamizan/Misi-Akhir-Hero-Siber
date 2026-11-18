"""
SIBERAKSI tema V3 - guna gambar bingkai anda sendiri.

Letakkan fail ini dalam folder YANG SAMA dengan 3 gambar:
  Futuristic_Cyan_Circuit_Landscape_Frame.png  (latar skrin)
  Futuristic_Cyber_Safety_Frame.png            (bingkai awan untuk panel)
  Siberaksi_Hero_Siber_Certificate.png         (sijil)
Tukar HTML di bawah jika fail permainan berada di tempat lain.
Gambar akan dimampatkan dan dimasukkan terus ke dalam HTML (satu fail sahaja).
"""
import base64, io, re
from pathlib import Path

HTML = Path('/mnt/data/SIBERAKSI_Misi_Akhir_Hero_Siber.html')
ASET = Path(__file__).resolve().parent
FILES = {
    '__SKY__': 'Futuristic_Cyan_Circuit_Landscape_Frame.png',
    '__CLOUD__': 'Futuristic_Cyber_Safety_Frame.png',
    '__CERT__': 'Siberaksi_Hero_Siber_Certificate.png',
}
START = '/* === TEMA SIBERAKSI V3 START === */'
END = '/* === TEMA SIBERAKSI V3 END === */'
FONT = ('<link rel="preconnect" href="https://fonts.googleapis.com">'
        '<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@600;800&display=swap" rel="stylesheet">')

CSS = r''':root{--navy:#123a8c;--royal:#1a5fe0;--cyan:#12d4f5;--gold:#ffd21f;--orange:#ff9a1f;--red:#ff4a5a;--green:#3ddc84;
 --font:"Baloo 2","Fredoka","Trebuchet MS","Comic Sans MS",Arial,sans-serif}
html{background:#19b6ee;min-height:100%}
html,body{margin:0;min-height:100vh}
body{color:var(--navy);font-family:var(--font);font-size:clamp(20px,2.3vw,28px);font-weight:700;line-height:1.4;
 background:#19b6ee url("__SKY__") center/cover no-repeat fixed}
p,li,label,span,div{font-size:inherit}

/* TAJUK GAYA POSTER: kuning + garis biru tua */
h1,.cert-title{font-weight:800;line-height:1.1;color:#ffe44d;font-size:clamp(40px,6vw,76px);
 -webkit-text-stroke:.07em #173f9e;paint-order:stroke fill;
 text-shadow:0 .08em 0 #b8560f,0 .16em .22em rgba(23,63,158,.45)}
h2{font-weight:800;font-size:clamp(32px,4.4vw,54px);color:var(--royal);text-shadow:0 3px 0 #fff,0 6px 0 rgba(23,63,158,.18)}
h3{font-weight:800;font-size:clamp(26px,3.2vw,40px);color:var(--navy)}
.subtitle{font-size:clamp(22px,2.8vw,34px);color:var(--navy)}

/* BAR ATAS */
.topbar{display:flex;flex-wrap:wrap;align-items:center;justify-content:space-between;gap:10px;
 margin:10px auto;max-width:1200px;padding:10px 20px 18px;border-radius:26px;border:4px solid var(--gold);color:#fff;
 font-size:clamp(20px,2.4vw,30px);
 background:repeating-linear-gradient(135deg,var(--gold) 0 12px,#173f9e 12px 24px) bottom/100% 8px no-repeat,
  radial-gradient(circle,rgba(18,212,245,.35) 0 3px,transparent 4px) 0 0/26px 26px,
  linear-gradient(180deg,#2a7ff0,#123a8c);
 box-shadow:0 7px 0 #0a2468,0 12px 22px rgba(10,50,130,.35)}
.pill{padding:.2em .9em;border-radius:999px;font-weight:800;color:#fff;border:3px solid var(--gold);
 background:linear-gradient(180deg,#2a6fe6,#123a8c);box-shadow:0 4px 0 #0a2468}

/* PANEL = BINGKAI AWAN */
.panel{position:relative;max-width:1200px;margin:clamp(10px,2vw,26px) auto;padding:7% 8% 10%;
 min-height:min(56vw,72vh);border:0;border-radius:0;box-shadow:none;color:var(--navy);
 background:url("__CLOUD__") center/100% 100% no-repeat;
 filter:drop-shadow(0 12px 18px rgba(10,50,130,.35))}
.panel:before,.panel:after{display:none}

/* BUTANG */
.btn,button{font-family:var(--font);font-weight:800;font-size:clamp(22px,2.6vw,32px);padding:.5em 1.4em;border-radius:999px;cursor:pointer}
.btn{color:#fff;border:4px solid var(--gold);text-shadow:0 2px 0 #0a2468;
 background:linear-gradient(180deg,#3d9cff,#1a5fe0 55%,#123a8c);
 box-shadow:inset 0 3px 0 rgba(255,255,255,.35),0 6px 0 #0a2468,0 10px 16px rgba(8,48,128,.3)}
.btn.gold{color:#6a3600;text-shadow:none;border-color:#ff9a1f;background:linear-gradient(180deg,#fff58a,#ffd633 52%,#ffad24);box-shadow:inset 0 3px 0 rgba(255,255,255,.5),0 6px 0 #c87912}
.btn.green{color:#064a36;text-shadow:none;background:linear-gradient(180deg,#a4f77e,#4cda79 55%,#18ad77);box-shadow:inset 0 3px 0 rgba(255,255,255,.45),0 6px 0 #12825b}
.btn.red{background:linear-gradient(180deg,#ff9a91,#ff5a70 55%,#e03a6c);box-shadow:inset 0 3px 0 rgba(255,255,255,.35),0 6px 0 #a52c5b}
.btn.light{color:var(--navy);text-shadow:none;background:linear-gradient(180deg,#bff3ff,#59d8f2 55%,#2aa8e8);box-shadow:inset 0 3px 0 rgba(255,255,255,.5),0 6px 0 #0877b6}
.btn:hover{transform:translateY(-3px) scale(1.03);filter:brightness(1.07)}
.btn:active{transform:translateY(3px)}

/* KAD PETA & BELAJAR */
.map-card,.learn-card{padding:14px 18px;border-radius:24px;border:4px solid var(--gold);color:#fff;
 background:radial-gradient(circle,rgba(255,255,255,.2) 0 3px,transparent 4px) 0 0/24px 24px,linear-gradient(145deg,#2a8cf0,#123a8c);
 box-shadow:0 7px 0 #0a2468,0 10px 16px rgba(7,55,130,.3)}
.map-card:nth-child(4n+2),.learn-card:nth-child(4n+2){background:radial-gradient(circle,rgba(255,255,255,.2) 0 3px,transparent 4px) 0 0/24px 24px,linear-gradient(145deg,#2fdc9b,#0f8aa8)}
.map-card:nth-child(4n+3),.learn-card:nth-child(4n+3){background:radial-gradient(circle,rgba(255,255,255,.2) 0 3px,transparent 4px) 0 0/24px 24px,linear-gradient(145deg,#ffb142,#ee5d7a)}
.map-card:nth-child(4n+4),.learn-card:nth-child(4n+4){background:radial-gradient(circle,rgba(255,255,255,.2) 0 3px,transparent 4px) 0 0/24px 24px,linear-gradient(145deg,#a98ff8,#4a5fd0)}
.map-card strong,.learn-card b{font-size:clamp(24px,2.8vw,34px);color:#fff58a;text-shadow:0 2px 0 #0a2468}
.map-card small{font-size:clamp(18px,2.1vw,24px);color:#fff}

/* JAWAPAN */
.answer{font-family:var(--font);font-weight:800;font-size:clamp(22px,2.6vw,32px);padding:.6em 1.1em;border-radius:999px;border:4px solid var(--gold);color:#fff;text-align:left;
 text-shadow:0 2px 0 #0a2468;background:linear-gradient(180deg,#3d9cff,#1a5fe0 55%,#123a8c);
 box-shadow:inset 0 3px 0 rgba(255,255,255,.3),0 6px 0 #0a2468,0 9px 14px rgba(8,48,128,.28)}
.answer:nth-child(2){background:linear-gradient(180deg,#52e8c0,#17b4a0 55%,#0b7f95)}
.answer:nth-child(3){background:linear-gradient(180deg,#ffc15e,#ff8a4a 55%,#e0507a)}
.answer:nth-child(4){background:linear-gradient(180deg,#b9a2ff,#7b72f0 55%,#4658c8)}
.answer:hover{background:linear-gradient(180deg,#fff58a,#ffc13a);color:#6a3600;text-shadow:none;transform:translateY(-3px) scale(1.02)}

/* NOTA & MAKLUM BALAS */
.note{font-size:clamp(20px,2.4vw,30px);padding:12px 20px;border-radius:20px;border:3px solid var(--orange);color:#6a3600;
 background:linear-gradient(110deg,#ffe86a,#ffc03a);box-shadow:0 5px 0 #c87912}
.feedback{font-size:clamp(22px,2.6vw,32px);font-weight:800;padding:12px 20px;border-radius:20px;border:4px solid var(--gold);color:#fff;text-shadow:0 2px 0 rgba(0,0,0,.25)}
.feedback.good{background:linear-gradient(130deg,#39d97e,#16c4aa,#0b9fb0)}
.feedback.bad{background:linear-gradient(130deg,#ff8b78,#f45b79,#c94cb0)}
.reward{font-size:clamp(60px,10vw,120px);filter:drop-shadow(0 8px 5px rgba(23,64,120,.6))}

/* SIJIL: GAMBAR SIJIL + NAMA DI KOTAK */
.certificate{container-type:inline-size;position:relative;width:min(100%,1100px);aspect-ratio:3/2;margin:16px auto;padding:0;border:0;border-radius:24px;overflow:hidden;
 color:var(--navy);background:url("__CERT__") center/100% 100% no-repeat;box-shadow:0 14px 30px rgba(10,50,130,.4)}
.certificate h2,.certificate .cert-title,.certificate p{display:none}
.cert-name{position:absolute;left:25.8%;top:38.9%;width:46%;height:8.8%;margin:0;padding:0 2%;display:flex;align-items:center;justify-content:center;
 border:0;background:transparent;color:var(--navy);font-family:var(--font);font-weight:800;font-size:4.2cqw;text-align:center;text-shadow:none;white-space:nowrap;overflow:hidden;-webkit-text-stroke:0}

/* BORANG */
input,select,textarea{font-family:var(--font);font-size:clamp(22px,2.6vw,32px);font-weight:800;padding:.4em .8em;color:var(--navy);background:#fff6c2;border:4px solid var(--orange);border-radius:18px}
::placeholder{color:#a8741a}
.footer{font-size:clamp(18px,2vw,24px);color:#fff;text-shadow:0 2px 0 #0a2468}
'''


def data_uri(path):
    raw = path.read_bytes()
    try:
        from PIL import Image
        im = Image.open(io.BytesIO(raw)).convert('RGB')
        if im.width > 1600:
            im = im.resize((1600, round(im.height * 1600 / im.width)))
        buf = io.BytesIO()
        im.save(buf, 'WEBP', quality=85)
        return 'data:image/webp;base64,' + base64.b64encode(buf.getvalue()).decode()
    except ImportError:
        return 'data:image/png;base64,' + base64.b64encode(raw).decode()


css = CSS
for token, name in FILES.items():
    f = ASET / name
    if not f.exists():
        raise SystemExit(f'Gambar tidak dijumpai: {f}')
    css = css.replace(token, data_uri(f))

s = HTML.read_text(encoding='utf-8')
s = re.sub(r'/\* === TEMA (?:CERIA )?SIBERAKSI V[23] START === \*/.*?/\* === TEMA (?:CERIA )?SIBERAKSI V[23] END === \*/\n?', '', s, flags=re.S)
if 'family=Baloo+2' not in s:
    s = s.replace('</head>', FONT + '</head>', 1)
s = s.replace('</style>', START + '\n' + css + '\n' + END + '\n</style>', 1)
HTML.write_text(s, encoding='utf-8')
print('Tema V3 siap: bingkai awan, latar langit litar, sijil bergambar, tulisan besar.')
