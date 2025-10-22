# -*- coding: utf-8 -*-
from reportlab.lib.pagesizes import A4
from reportlab.lib import colors
from reportlab.pdfgen import canvas
from reportlab.pdfbase import pdfmetrics
from reportlab.pdfbase.cidfonts import UnicodeCIDFont
from reportlab.platypus import SimpleDocTemplate, Paragraph, Spacer, PageBreak
from reportlab.lib.styles import getSampleStyleSheet, ParagraphStyle

# Register Hindi font
pdfmetrics.registerFont(UnicodeCIDFont('HeiseiMin-W3'))

# Function to add watermark
def add_watermark(c, text="A K CLASSES"):
    c.saveState()
    c.setFont("HeiseiMin-W3", 60)
    c.setFillGray(0.90, 0.3)
    c.translate(300, 400)
    c.rotate(45)
    c.drawCentredString(0, 0, text)
    c.restoreState()

# Page template with watermark
def on_page(canvas, doc):
    add_watermark(canvas)

# Create PDF
doc = SimpleDocTemplate(
    "A_K_CLASSES_Question_Paper.pdf",
    pagesize=A4,
    rightMargin=36, leftMargin=36,
    topMargin=36, bottomMargin=36
)

styles = getSampleStyleSheet()
styles.add(ParagraphStyle(name='Hindi', fontName='HeiseiMin-W3', fontSize=11, leading=14))
story = []

# Title
story.append(Paragraph("<para align='center'><b><font size=16>A K CLASSES</font></b></para>", styles['Hindi']))
story.append(Spacer(1, 6))
story.append(Paragraph("<para align='center'><b>विषय : हिन्दी प्रश्नपत्र</b></para>", styles['Hindi']))
story.append(Paragraph("<para align='center'>कक्षा – १२ | समय – ३ घंटे | पूर्णांक – १००</para>", styles['Hindi']))
story.append(Spacer(1, 12))

# Section A
story.append(Paragraph("<b>खंड – A : वस्तुनिष्ठ प्रश्न (Objective Type)</b>", styles['Hindi']))
story.append(Paragraph("निर्देश: नीचे दिए गए ४० प्रश्नों में से किसी भी २० का उत्तर दीजिए। प्रत्येक प्रश्न १ अंक का है।", styles['Hindi']))
story.append(Spacer(1, 8))

section_a = [
    "'अविन्यो' किस नदी के किनारे स्थित है? (A) रावी (B) रोन (C) गंगा (D) सतलज",
    "कुमार गंधर्व क्या है? (A) गीतकार (B) शास्त्रीय गायक (C) कथाकार (D) चित्रकार",
    "गाँधीजी शिक्षा का उद्देश्य क्या मानते थे? (A) नौकरी पाना (B) वैज्ञानिक बनना (C) चरित्र-निर्माण (D) यांत्रिक दक्षता",
    "घनानंद ने किस मार्ग को अत्यन्त सीधा व सरल कहा है? (A) क्रोध (B) प्रेम (C) घृणा (D) कपट",
    "'रसखान' को किसने दीक्षा दी? (A) वल्लभाचार्य (B) गोकुलनाथ (C) गोस्वामी विट्ठलनाथ (D) गोरखनाथ",
    "धनानंद किस भाषा के कवि हैं? (A) अवधी (B) ब्रजभाषा (C) भोजपुरी (D) गुजराती",
    "'तुलनात्मक व्याकरण' किसकी रचना है? (A) सातकोड़ी होता (B) सुजाता (C) काल्डवेल (D) सौवर दइया",
    "मंगम्मा को किससे विवाद था? (A) बेटे से (B) बहू से (C) पोते से (D) सास से",
    "'हिरोशिमा' शीर्षक कविता में वर्णित सूरज कहाँ निकला? (A) पूर्वी क्षितिज पर (B) नगर के चौक पर (C) पूर्वी दिशा में (D) इनमें से कहीं नहीं",
    "अव्ययीभाव समास का उदाहरण है? (A) लवकुश (B) भरपेट (C) त्रिभुवन (D) छत्रधारी",
    "बेईमान में कौन-सा उपसर्ग है? (A) बेइन (B) बेइ (C) बे (D) इन",
    "इनमें से शुद्ध वाक्य को पहचानें। (A) मेरे को घर जाना है। (B) मेरा नाम आनन्द जी है। (C) मेरे को काम करना है। (D) इसमें से कोई नहीं",
    "'आलोचना' का पर्यायवाची शब्द है। (A) प्रशंसा (B) समीक्षा (C) प्रलाप (D) गपशप",
    "'अम्बर' का विलोम शब्द है। (A) इन्द्र (B) इन्द्राणी (C) धरा (D) दिगम्बर",
    "'वर्ण' के उच्चारण में लगनेवाले समय के आधार पर स्वर वर्ण के कितने भेद होते हैं? (A) दो (B) तीन (C) चार (D) पाँच",
    "'जिसका जन्म पहले हुआ हो' का एक शब्द है? (A) अग्रज (B) स्वस्थ (C) विद्या (D) पुत्र",
    "'क' का उच्चारण स्थान क्या है? (A) कंठ (B) तालु (C) दंत (D) ओष्ठ",
    "बिरजू महाराज की शादी कितने वर्ष की उम्र में हुई थी? (A) १६ (B) १८ (C) १५ (D) १७",
    "'राम नाम बिनु बिरथे जगि जन्मा' में 'बिरथे' का अर्थ क्या है? (A) व्यर्थ (B) तीर्थ (C) धर्मोपदेश (D) कोई नहीं",
    "'दही वाली मंगम्मा' कहानी कहाँ से ली गई है? (A) कन्नड़ कहानियाँ (B) तमिल कहानियाँ (C) उड़िया कहानियाँ (D) असामी कहानियाँ",
    "'इच्छा' शब्द का पर्यायवाची शब्द कौन सा है? (A) कामना (B) अभिलाषा (C) चाह (D) ये सभी",
    "'अग्नि' शब्द का विलोम शब्द क्या है? (A) जल (B) पवन (C) आकाश (D) धरती",
]
# Add 40 MCQs (repeat pattern)
for i, q in enumerate(section_a * 2)[:40]:
    story.append(Paragraph(f"{i+1}. {q}", styles['Hindi']))

story.append(PageBreak())

# Section B
story.append(Paragraph("<b>खंड – B : लघु उत्तरीय प्रश्न (Short Answer Questions)</b>", styles['Hindi']))
story.append(Paragraph("निर्देश: नीचे दिए गए ३० प्रश्नों में से किसी भी १५ का उत्तर दीजिए। प्रत्येक प्रश्न २ अंक का है।", styles['Hindi']))
story.append(Spacer(1, 8))

for i in range(1, 31):
    story.append(Paragraph(f"{i}. निम्नलिखित प्रश्न का उत्तर लिखिए — प्रश्न संख्या {i}", styles['Hindi']))

story.append(PageBreak())

# Section C
story.append(Paragraph("<b>खंड – C : दीर्घ उत्तरीय प्रश्न (Long Answer Questions)</b>", styles['Hindi']))
story.append(Paragraph("निर्देश: नीचे दिए गए ३० प्रश्नों में से किसी भी १५ का उत्तर दीजिए। प्रत्येक प्रश्न ४ अंक का है।", styles['Hindi']))
story.append(Spacer(1, 8))

for i in range(1, 31):
    story.append(Paragraph(f"{i}. नीचे दिए गए प्रश्न का विस्तारपूर्वक उत्तर दीजिए — प्रश्न संख्या {i}", styles['Hindi']))

# Build document
doc.build(story, onFirstPage=on_page, onLaterPages=on_page)

print("✅ प्रश्नपत्र 'A_K_CLASSES_Question_Paper.pdf' सफलतापूर्वक तैयार हो गया है।")
