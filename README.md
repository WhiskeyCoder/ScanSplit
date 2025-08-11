# 📚 ScanSplit

**ScanSplit** is a Python tool that converts dual-page scanned PDFs or images into single-page PDFs — perfect for fixing scanned books, magazines, and archival documents.  
It can optionally enhance text for better OCR accuracy, handles skewed pages, shadows in the gutter, and maintains correct reading order.

---

## ✨ Features
- **Dual-page → Single-page** splitting with correct left/right reading order.
- **Shadow-aware splitting** to detect the center fold, even with uneven scans.
- **Optional text enhancement** for poor-quality scans (contrast boost, denoise, subtle sharpening).
- **Batch mode** for processing entire directories.
- **Supports PDFs and images** (`.pdf`, `.jpg`, `.png`, `.tiff`, `.bmp`).
- **Customizable DPI** for high-quality output.

---

## 📦 Requirements

Install dependencies with:
```bash
pip install opencv-python pillow pymupdf reportlab numpy
```

## 🚀 Usage
Basic syntax
```bash
python double_page_scan_to_single.py [files or directories] [options]
```
Examples:
```bash
# Split pages without text enhancement (RECOMMENDED for normal scans)
python double_page_scan_to_single.py "book.pdf" --no-enhance

# Split all PDFs in the current directory
python double_page_scan_to_single.py --no-enhance

# Split with text enhancement (use only for poor scans)
python double_page_scan_to_single.py "old_book.pdf"

# Process multiple PDFs without enhancement
python double_page_scan_to_single.py *.pdf --no-enhance

# Process at high DPI without enhancement
python double_page_scan_to_single.py "book.pdf" --dpi 600 --no-enhance
```

## ⚙ Options
Option	Description
--output / -o	Output directory (default: scan_fix_output)
--no-enhance	Skip text enhancement
--dpi	DPI for PDF rendering (default: 300)
--shadow-threshold	Darkness threshold for shadow detection (0-255, default: 50)
--min-shadow-height	Minimum shadow height ratio (default: 0.3)
--debug	Enable debug logging

## 📂 Output
Processed files are saved to the specified output folder (default: scan_fix_output/).
Output filenames follow the pattern:
```
originalfilename_split.pdf
```
Pages are split into left page first, then right page order.


## 🛠 How It Works
1. PDF/Image Conversion → Converts each page to an image at the specified DPI.
2. Center Split Detection → Uses shadow analysis or edge detection to find the page fold.
3. Optional Enhancement → Improves text readability for OCR.
4. Page Export → Saves split pages into a new single-page-per-sheet PDF.

## 🔍 When to Use --no-enhance
- For clean, modern scans, always use --no-enhance for best results.
- Use enhancement only for faded or poor-quality scans — over-processing can make text look unnatural.

## 📜 License
MIT License — free to use, modify, and distribute.
