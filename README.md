# torch_scatter-Wheel

Custom **torch_scatter** Wheel für CUDA 13 + Blackwell GPU (sm_120).

Optimiert für **HuggingFace ZeroGPU** und **PSHuman** auf Blackwell Hardware.

## 🎯 Specs

| Komponente | Version |
|---|---|
| **Python** | 3.10 |
| **PyTorch** | 2.11.0 + cu130 |
| **CUDA** | 13 |
| **GPU Arch** | **12.0 (Blackwell / ONLY)** |
| **torch_scatter** | latest (konfigurierbar) |

## 🚀 Workflow

Der GitHub Actions Workflow (`build_torch_scatter.yml`) baut das Wheel automatisch.

**Manuell triggern:**
1. GitHub → **Actions** → *Build torch_scatter Wheel*
2. **Run workflow** → Optional: torch_scatter version eingeben (Branch/Tag/Commit)
3. **Run** → 20–40 Min. warten

**Release:**
Nach erfolgreichem Build wird ein GitHub Release mit dem Wheel erstellt.

## 📦 Installation

Die `.whl`-URL aus dem Release kopieren und in `requirements.txt` eintragen:

```
https://github.com/Painter3000/torch_scatter_wheel/releases/download/torch_scatter-torch2.11.0-cu128/torch_scatter-XXX-cp310-cp310-linux_x86_64.whl
```

Dann wie gewohnt installieren:
```bash
pip install -r requirements.txt
```

## ⚙️ Build-Details

- ✅ `--no-build-isolation` → exakt torch 2.11.0, kein Downgrade
- ✅ `--index-url cu128` → CUDA-Wheel, nicht CPU
- ✅ `FORCE_CUDA=1` → Kompilierung ohne physische GPU
- ✅ `sm_120` enthalten → Blackwell RTX PRO 6000 unterstützt

## 🔗 Verwendung in PSHuman

Ersetze in PSHuman `requirements.txt`:
```diff
- # disabled_blackwell_incompatible: torch_scatter
+ https://github.com/Painter3000/torch_scatter_wheel/releases/download/torch_scatter-torch2.11.0-cu130/torch_scatter-XXX-cp310-cp310-linux_x86_64.whl
```

---

**Status:** ⏳ Build ausstehend

Teil der Blackwell-Kompatibilisierungs-Pipeline für PSHuman.
