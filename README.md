// QuestionPaperGenerator.jsx
import React, { useState, useRef } from "react";
import Tesseract from "tesseract.js";
import jsPDF from "jspdf";

export default function QuestionPaperGenerator() {
  const [questions, setQuestions] = useState([]);
  const [loadingOCR, setLoadingOCR] = useState(false);
  const [inputText, setInputText] = useState("");
  const [watermark, setWatermark] = useState("");
  const [lineSpacing, setLineSpacing] = useState(1.5);
  const [customInfo, setCustomInfo] = useState("");
  const [previewHtml, setPreviewHtml] = useState("");
  const fileInputRef = useRef();

  // OCR scan image, extract text questions
  const handleScan = () => {
    const file = fileInputRef.current.files[0];
    if (!file) return alert("Select an image to scan.");
    setLoadingOCR(true);
    Tesseract.recognize(file, "eng")
      .then(({ data: { text } }) => {
        setInputText(text);
        const parsedQuestions = text.split("
").filter((q) => q.trim() !== "");
        setQuestions(parsedQuestions);
      })
      .finally(() => setLoadingOCR(false));
  };

  // Update preview HTML based on current inputs
  const updatePreview = () => {
    const questionHtml = questions
      .map(
        (q, idx) => `<p style="margin-bottom:${lineSpacing}em;">${idx + 1}. ${q}</p>`
      )
      .join("");
    const watermarkHtml = watermark
      ? `<div style="position:absolute;top:50%;left:50%;transform:translate(-50%, -50%) rotate(-45deg);opacity:0.1;font-size:5em;color:#000;">${watermark}</div>`
      : "";
    const customInfoHtml = `<div>${customInfo}</div>`;
    const fullHtml = `
      <div style="position:relative; padding:40px; font-family:Arial; font-size:14pt;">
        ${watermarkHtml}
        ${customInfoHtml}
        ${questionHtml}
      </div>`;
    setPreviewHtml(fullHtml);
  };

  // Download the question paper as A4 PDF
  const downloadPDF = () => {
    const doc = new jsPDF({
      unit: "pt",
      format: "a4",
    });
    doc.setFont("times", "normal");
    doc.setFontSize(12);
    let y = 40;
    if (watermark) {
      doc.setTextColor(0, 0, 0, 15);
      doc.text(watermark, 210, 420, { angle: 45 });
      doc.setTextColor(0, 0, 0, 255);
    }
    if (customInfo) {
      doc.text(customInfo, 40, y);
      y += 40;
    }
    questions.forEach((q, i) => {
      doc.text(`${i + 1}. ${q}`, 40, y);
      y += 14 * lineSpacing;
      if (y > 800) {
        doc.addPage();
        y = 40;
      }
    });
    doc.save("question-paper.pdf");
  };

  return (
    <div style={{ maxWidth: "900px", margin: "auto", padding: "20px" }}>
      <h2>Question Paper Generator</h2>

      <div>
        <strong>Scan questions from image (JPEG/PNG): </strong>
        <input type="file" accept="image/*" ref={fileInputRef} />
        <button onClick={handleScan} disabled={loadingOCR}>
          {loadingOCR ? "Scanning..." : "Scan"}
        </button>
      </div>

      <div style={{ marginTop: "20px" }}>
        <strong>Or paste questions (one per line):</strong>
        <textarea
          rows="6"
          style={{ width: "100%" }}
          value={inputText}
          onChange={(e) => {
            setInputText(e.target.value);
            setQuestions(e.target.value.split("
").filter((q) => q.trim() !== ""));
          }}
        />
      </div>

      <div style={{ marginTop: "20px" }}>
        <label>Watermark Text:</label> <br />
        <input
          type="text"
          value={watermark}
          onChange={(e) => setWatermark(e.target.value)}
          style={{ width: "100%" }}
          placeholder="Enter watermark text"
        />
      </div>

      <div style={{ marginTop: "20px" }}>
        <label>Custom Information (will appear anywhere on paper):</label>
        <textarea
          rows="3"
          style={{ width: "100%" }}
          value={customInfo}
          onChange={(e) => setCustomInfo(e.target.value)}
          placeholder="Add any extra info"
        />
      </div>

      <div style={{ marginTop: "20px" }}>
        <label>Line Spacing (between questions):</label> <br />
        <input
          type="number"
          value={lineSpacing}
          min="1"
          max="5"
          step="0.1"
          onChange={(e) => setLineSpacing(parseFloat(e.target.value))}
        />
      </div>

      <div style={{ marginTop: "20px" }}>
        <button onClick={updatePreview}>Preview Question Paper</button>
        <button onClick={downloadPDF} style={{ marginLeft: "10px" }}>
          Download PDF (A4)
        </button>
      </div>

      <div
        style={{
          marginTop: "40px",
          border: "1px solid #ccc",
          minHeight: "300px",
          position: "relative",
          backgroundColor: "#fff",
          padding: "10px",
        }}
        dangerouslySetInnerHTML={{ __html: previewHtml }}
      />
    </div>
  );
}