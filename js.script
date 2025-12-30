// Mobile nav
const toggle = document.querySelector(".nav-toggle");
const menu = document.querySelector("#nav-menu");

if (toggle && menu) {
  toggle.addEventListener("click", () => {
    const isOpen = menu.classList.toggle("open");
    toggle.setAttribute("aria-expanded", String(isOpen));
  });

  menu.querySelectorAll("a").forEach(a => {
    a.addEventListener("click", () => {
      menu.classList.remove("open");
      toggle.setAttribute("aria-expanded", "false");
    });
  });
}

// Footer year
const y = document.querySelector("#year");
if (y) y.textContent = new Date().getFullYear();

// Publications: search + filter
const pubSearch = document.querySelector("#pubSearch");
const pubFilter = document.querySelector("#pubFilter");
const pubItems = Array.from(document.querySelectorAll(".pub-item"));

function applyPubFilter(){
  const q = (pubSearch?.value || "").trim().toLowerCase();
  const type = pubFilter?.value || "all";

  pubItems.forEach(item => {
    const text = item.innerText.toLowerCase();
    const itemType = item.dataset.type || "";
    const okType = (type === "all") || (itemType === type);
    const okQuery = !q || text.includes(q);
    item.style.display = (okType && okQuery) ? "" : "none";
  });
}

pubSearch?.addEventListener("input", applyPubFilter);
pubFilter?.addEventListener("change", applyPubFilter);
applyPubFilter();

/**
 * Anti-spam email:
 * - Do NOT place the full address as plain text in HTML.
 * - Assemble it at runtime and set mailto + visible label.
 *
 * IMPORTANT: If you ever want to change the public email, edit user/domain below.
 */
(function antiSpamEmail(){
  const el = document.getElementById("emailLink");
  if (!el) return;

  const user = "stsamiotis95";
  const domain = "gmail.com";
  const address = `${user}@${domain}`;

  el.textContent = `${user} [at] ${domain}`;
  el.href = `mailto:${address}`;
})();

// i18n (EL/EN)
const dict = {
  el: {
    nav_about: "Προφίλ",
    nav_research: "Έρευνα",
    nav_pubs: "Δημοσιεύσεις",
    nav_talks: "Ομιλίες",
    nav_exp: "Εμπειρία",
    nav_contact: "Επικοινωνία",

    hero_kicker: "Υποψήφιος Διδάκτωρ · Πανεπιστήμιο Ιωαννίνων (Φιλολογία — Γλωσσολογία)",
    hero_name: "Σταύρος",
    hero_surname: "Σαμιώτης",
    hero_lead: "Θεωρητικός γλωσσολόγος με έμφαση στη διεπαφή Σύνταξης–Πραγματολογίας και στη διανομή/οντολογία αναφορικών (anaphoric) ονοματικών. Ενδιαφέροντα: Binding Theory, Logophoricity, Anaphora.",

    cta_cv: "CV (PDF)",
    cta_pubs: "Δημοσιεύσεις",

    meta_affil_label: "Ίδρυμα:",
    meta_affil_value: "Πανεπιστήμιο Ιωαννίνων / Τμήμα Φιλολογίας — Τομέας Γλωσσολογίας",
    meta_interests_label: "Ενδιαφέροντα:",
    meta_links_label: "Links:",

    quick_title: "Σύντομο",
    quick_text: "Υποψήφιος διδάκτωρ στη Γλωσσολογία (Παν. Ιωαννίνων). Μελετώ φαινόμενα αναφοράς/αντωνυμίας, λογοφορικότητας και locality στη Νέα Ελληνική, με έμφαση στο στοιχείο ο/τον ίδιο.",

    about_title: "Ακαδημαϊκό Προφίλ",
    about_sub: "Εκπαίδευση, θεματικές, σύντομο bio.",
    about_bio_title: "Bio",
    about_bio_p1: "Είμαι θεωρητικός γλωσσολόγος (MA) και υποψήφιος διδάκτωρ στο Πανεπιστήμιο Ιωαννίνων. Το ερευνητικό μου ενδιαφέρον εστιάζει στη διεπαφή Σύνταξης–Πραγματολογίας, με ειδική έμφαση στη διανομή και οντολογία αναφορικών ονοματικών.",
    about_supervisor: "PhD supervisor: Dr. Marika Lekakou (Associate Professor).",
    about_edu_title: "Εκπαίδευση",
    about_further_title: "Summer/Winter Schools",
    about_lang_title: "Γλώσσες",
    about_scholarship: "Scholarship: Erasmus+ (IKY), Sep–Dec 2017.",

    edu_phd: "PhD στη Γλωσσολογία",
    edu_phd_thesis: "Διατριβή: “Logophoricity, Focus and Locality: the case of the Modern Greek element ‘o idhjos’”.",
    edu_ma: "ΜΑ στη Θεωρητική Γλωσσολογία",
    edu_ma_thesis: "Διπλωματική: “The distribution and semantic-syntactic properties of (o/i/to) idhjos/-a/-o”.",
    edu_ba: "Πτυχίο Φιλολογίας",
    edu_ba_note: "Νεοελληνική & Μεσαιωνική ελληνική γλώσσα και λογοτεχνία.",

    lang_el: "Ελληνικά",
    lang_el_level: "Μητρική",
    lang_en: "Αγγλικά",
    lang_de: "Γερμανικά",

    research_title: "Έρευνα",
    research_sub: "Θεματικές και εστίαση.",
    research_bt: "Περιορισμοί δέσμευσης/συν-αναφοράς, referential dependence και locality στο ονοματικό πεδίο.",
    research_log: "Κωδικοποίηση οπτικής γωνίας/“speaker” σε δομές λόγου και σχέση με στοιχεία όπως ο ίδιος στη Νέα Ελληνική.",
    research_ana: "Αναφορά/αντωνυμία, anaphoric nominals και αλληλεπίδραση με focus/πραγματολογία.",

    pubs_title: "Δημοσιεύσεις",
    pubs_sub: "Αναζήτηση & φίλτρο ανά τύπο.",
    pubs_search_ph: "Αναζήτηση (τίτλος, έτος, venue, keyword)...",
    pubs_filter_all: "Όλα",
    pubs_filter_proc: "Proceedings",
    pubs_filter_journal: "Journal",
    pubs_filter_thesis: "Thesis",
    pubs_filter_other: "Other",
    pubs_tip: "Αν θέλεις, μπορώ να προσθέσω κουμπιά “PDF/Slides/DOI” όπου υπάρχουν διαθέσιμα links.",

    talks_title: "Ομιλίες & Presentations",
    talks_sub: "Επιλεγμένες παρουσιάσεις από συνέδρια.",

    exp_title: "Εμπειρία & Δραστηριότητα",
    exp_sub: "Research collaborations, εργασία, εθελοντισμός.",
    exp_collab_title: "Research collaborations",
    exp_work_title: "Εργασιακή εμπειρία",
    exp_vol_title: "Εθελοντισμός",
    exp_misc_title: "Άλλα",
    exp_military: "Στρατιωτική θητεία: May 2018–Jan 2019",
    exp_sports_note: "(Αν θέλεις, προσθέτω ξεχωριστή ενότητα “Sport distinctions” με τις διακρίσεις κωπηλασίας.)",

    contact_title: "Επικοινωνία",
    contact_sub: "Email με anti-spam εμφάνιση + links.",
    contact_details_title: "Στοιχεία",
    contact_email_label: "Email:",
    contact_email_hint: "— (anti-spam)",
    contact_phone_label: "Τηλ.:",
    contact_city_label: "Πόλη:",
    contact_privacy_note: "Αν προτιμάς να μη φαίνεται ούτε το τηλέφωνο/πόλη, το αφαιρώ.",
    contact_links_title: "Ακαδημαϊκά Προφίλ"
  },

  en: {
    nav_about: "About",
    nav_research: "Research",
    nav_pubs: "Publications",
    nav_talks: "Talks",
    nav_exp: "Experience",
    nav_contact: "Contact",

    hero_kicker: "PhD Candidate · University of Ioannina (Philology — Linguistics)",
    hero_name: "Stavros",
    hero_surname: "Samiotis",
    hero_lead: "Theoretical linguist (MA) focusing on the Syntax–Pragmatics interface and the distribution/ontology of anaphoric nominals. Interests: Binding Theory, Logophoricity, Anaphora.",

    cta_cv: "CV (PDF)",
    cta_pubs: "Publications",

    meta_affil_label: "Affiliation:",
    meta_affil_value: "University of Ioannina / Dept. of Philology — Division of Linguistics",
    meta_interests_label: "Interests:",
    meta_links_label: "Links:",

    quick_title: "At a glance",
    quick_text: "PhD candidate in Linguistics (University of Ioannina). I work on reference/anaphora, logophoricity, and locality in Modern Greek, with emphasis on the element o/ton idhjos.",

    about_title: "Academic Profile",
    about_sub: "Education, focus, short bio.",
    about_bio_title: "Bio",
    about_bio_p1: "I am a theoretical linguist (MA) and a PhD candidate at the University of Ioannina. My research focuses on the Syntax–Pragmatics interface, with special emphasis on the distribution and ontology of anaphoric nominals.",
    about_supervisor: "PhD supervisor: Dr. Marika Lekakou (Associate Professor).",
    about_edu_title: "Education",
    about_further_title: "Summer/Winter Schools",
    about_lang_title: "Languages",
    about_scholarship: "Scholarship: Erasmus+ (IKY), Sep–Dec 2017.",

    edu_phd: "PhD in Linguistics",
    edu_phd_thesis: "Thesis: “Logophoricity, Focus and Locality: the case of the Modern Greek element ‘o idhjos’”.",
    edu_ma: "MA in Theoretical Linguistics",
    edu_ma_thesis: "Thesis: “The distribution and semantic-syntactic properties of (o/i/to) idhjos/-a/-o”.",
    edu_ba: "BA in Philology",
    edu_ba_note: "Modern & Medieval Greek language and literature.",

    lang_el: "Greek",
    lang_el_level: "Native",
    lang_en: "English",
    lang_de: "German",

    research_title: "Research",
    research_sub: "Themes and focus.",
    research_bt: "Binding/co-reference constraints, referential dependence, and locality in the nominal domain.",
    research_log: "How perspective/‘speaker’ is encoded in discourse, and its link to elements such as idhjos in Modern Greek.",
    research_ana: "Reference/anaphora, anaphoric nominals, and interactions with focus/pragmatics.",

    pubs_title: "Publications",
    pubs_sub: "Search & filter by type.",
    pubs_search_ph: "Search (title, year, venue, keyword)...",
    pubs_filter_all: "All",
    pubs_filter_proc: "Proceedings",
    pubs_filter_journal: "Journal",
    pubs_filter_thesis: "Thesis",
    pubs_filter_other: "Other",
    pubs_tip: "If you want, I can add “PDF/Slides/DOI” buttons wherever links are available.",

    talks_title: "Talks & Presentations",
    talks_sub: "Selected conference presentations.",

    exp_title: "Experience & Service",
    exp_sub: "Research collaborations, work, volunteering.",
    exp_collab_title: "Research collaborations",
    exp_work_title: "Work experience",
    exp_vol_title: "Volunteering",
    exp_misc_title: "Other",
    exp_military: "Military service: May 2018–Jan 2019",
    exp_sports_note: "(If you want, I can add a dedicated “Sport distinctions” section for rowing.)",

    contact_title: "Contact",
    contact_sub: "Anti-spam email display + links.",
    contact_details_title: "Details",
    contact_email_label: "Email:",
    contact_email_hint: "— (anti-spam)",
    contact_phone_label: "Phone:",
    contact_city_label: "City:",
    contact_privacy_note: "If you prefer, I can remove phone/city.",
    contact_links_title: "Academic Profiles"
  }
};

function setLanguage(lang){
  document.documentElement.lang = lang;

  document.querySelectorAll("[data-i18n]").forEach(el => {
    const key = el.getAttribute("data-i18n");
    if (dict[lang] && dict[lang][key]) el.textContent = dict[lang][key];
  });

  document.querySelectorAll("[data-i18n-placeholder]").forEach(el => {
    const key = el.getAttribute("data-i18n-placeholder");
    if (dict[lang] && dict[lang][key]) el.setAttribute("placeholder", dict[lang][key]);
  });

  document.querySelectorAll(".chip[data-lang]").forEach(btn => {
    const active = btn.getAttribute("data-lang") === lang;
    btn.setAttribute("aria-pressed", String(active));
  });

  localStorage.setItem("lang", lang);
}

document.querySelectorAll(".chip[data-lang]").forEach(btn => {
  btn.addEventListener("click", () => setLanguage(btn.getAttribute("data-lang")));
});

const saved = localStorage.getItem("lang");
setLanguage(saved === "en" ? "en" : "el");
