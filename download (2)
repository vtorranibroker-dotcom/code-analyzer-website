/**
 * DESIGN SYSTEM: Industrial Precision
 * Movement: Swiss Grid / Industrial Design
 * Colors: Ivory #F5F4F0 bg, Near-black #1A1A1A text, Industrial Red #D4380D accent, Technical Blue #003A8C primary
 * Typography: Bebas Neue (display), Inter (body)
 * Layout: Asymmetric sections, large decorative numbers, thick rule separators
 */

import { useEffect, useRef, useState } from "react";

// ── Animated counter hook ──────────────────────────────────────────────────
function useCounter(target: number, duration = 1800, start = false) {
  const [value, setValue] = useState(0);
  useEffect(() => {
    if (!start) return;
    let startTime: number | null = null;
    const step = (timestamp: number) => {
      if (!startTime) startTime = timestamp;
      const progress = Math.min((timestamp - startTime) / duration, 1);
      setValue(Math.floor(progress * target));
      if (progress < 1) requestAnimationFrame(step);
    };
    requestAnimationFrame(step);
  }, [target, duration, start]);
  return value;
}

// ── Intersection observer hook ─────────────────────────────────────────────
function useInView(threshold = 0.2) {
  const ref = useRef<HTMLDivElement>(null);
  const [inView, setInView] = useState(false);
  useEffect(() => {
    const obs = new IntersectionObserver(
      ([entry]) => { if (entry.isIntersecting) setInView(true); },
      { threshold }
    );
    if (ref.current) obs.observe(ref.current);
    return () => obs.disconnect();
  }, [threshold]);
  return { ref, inView };
}

// ── Stat counter component ─────────────────────────────────────────────────
function StatCounter({ value, suffix, label }: { value: number; suffix: string; label: string }) {
  const { ref, inView } = useInView();
  const count = useCounter(value, 1600, inView);
  return (
    <div ref={ref} className="border-l-4 border-[#D4380D] pl-6">
      <div className="font-display text-6xl text-[#1A1A1A] leading-none">
        {count}{suffix}
      </div>
      <div className="text-sm text-[#555] mt-2 uppercase tracking-widest font-medium">{label}</div>
    </div>
  );
}

// ── Navbar ─────────────────────────────────────────────────────────────────
function Navbar() {
  const [scrolled, setScrolled] = useState(false);
  useEffect(() => {
    const handler = () => setScrolled(window.scrollY > 40);
    window.addEventListener("scroll", handler);
    return () => window.removeEventListener("scroll", handler);
  }, []);

  return (
    <nav
      className={`fixed top-0 left-0 right-0 z-50 transition-all duration-300 ${
        scrolled ? "bg-[#F5F4F0]/95 backdrop-blur-sm shadow-sm" : "bg-transparent"
      }`}
    >
      <div className="container flex items-center justify-between h-16">
        <div className="font-display text-2xl text-[#1A1A1A] tracking-wider">
          CODE<span className="text-[#D4380D]">PERF</span>
        </div>
        <div className="hidden md:flex items-center gap-8 text-sm font-medium text-[#1A1A1A]">
          <a href="#features" className="hover:text-[#D4380D] transition-colors">Funzionalità</a>
          <a href="#how-it-works" className="hover:text-[#D4380D] transition-colors">Come Funziona</a>
          <a href="#savings" className="hover:text-[#D4380D] transition-colors">Risparmio</a>
          <a href="#compare" className="hover:text-[#D4380D] transition-colors">Confronto</a>
        </div>
        <a
          href="#contact"
          className="bg-[#003A8C] text-[#F5F4F0] px-5 py-2 text-sm font-semibold hover:bg-[#002870] transition-colors"
        >
          Richiedi Demo
        </a>
      </div>
    </nav>
  );
}

// ── Hero Section ───────────────────────────────────────────────────────────
function Hero() {
  return (
    <section className="relative min-h-screen flex items-center overflow-hidden bg-[#F5F4F0]">
      {/* Background image */}
      <div className="absolute inset-0 z-0">
        <img
          src="https://d2xsxph8kpxj0f.cloudfront.net/310519663455238999/VxRZDeE7HcGjoa9uRc77vg/hero-bg-DvYaGao5hSD3jfVydGKzHT.png"
          alt=""
          className="w-full h-full object-cover opacity-20"
        />
        <div className="absolute inset-0 bg-gradient-to-r from-[#F5F4F0] via-[#F5F4F0]/80 to-[#F5F4F0]/30" />
      </div>

      <div className="container relative z-10 pt-24 pb-20">
        <div className="max-w-3xl">
          {/* Eyebrow */}
          <div className="flex items-center gap-3 mb-8">
            <div className="w-8 h-[3px] bg-[#D4380D]" />
            <span className="text-xs font-semibold uppercase tracking-[0.2em] text-[#D4380D]">
              Analisi Statica · Runtime · Costi Azure
            </span>
          </div>

          {/* Main title */}
          <h1 className="font-display text-[clamp(3.5rem,8vw,7rem)] leading-[0.95] text-[#1A1A1A] mb-6">
            ANALIZZATORE<br />
            <span className="text-[#003A8C]">MULTI-LINGUAGGIO</span><br />
            DI PERFORMANCE
          </h1>

          <hr className="rule-accent w-24 mb-8" />

          <p className="text-lg text-[#444] leading-relaxed max-w-xl mb-10">
            Identifica le inefficienze nel codice Python, Java e TypeScript.
            Quantifica il risparmio economico su Azure. Ottimizza prima di deployare.
          </p>

          {/* CTA buttons */}
          <div className="flex flex-wrap gap-4">
            <a
              href="#how-it-works"
              className="bg-[#003A8C] text-[#F5F4F0] px-8 py-4 font-semibold text-sm uppercase tracking-widest hover:bg-[#002870] transition-colors"
            >
              Scopri Come Funziona
            </a>
            <a
              href="#compare"
              className="border-2 border-[#1A1A1A] text-[#1A1A1A] px-8 py-4 font-semibold text-sm uppercase tracking-widest hover:bg-[#1A1A1A] hover:text-[#F5F4F0] transition-colors"
            >
              Confronta i Prodotti
            </a>
          </div>
        </div>
      </div>

      {/* Scroll indicator */}
      <div className="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-[#888]">
        <span className="text-xs uppercase tracking-widest">Scorri</span>
        <div className="w-[1px] h-10 bg-[#888] animate-pulse" />
      </div>
    </section>
  );
}

// ── Stats Bar ──────────────────────────────────────────────────────────────
function StatsBar() {
  return (
    <section className="bg-[#1A1A1A] py-14">
      <div className="container">
        <div className="grid grid-cols-2 md:grid-cols-4 gap-8 md:gap-0 md:divide-x md:divide-[#333]">
          {[
            { value: 3, suffix: "", label: "Linguaggi Supportati" },
            { value: 50, suffix: "%", label: "Efficienza Massima" },
            { value: 8760, suffix: "h", label: "Calcolo Annuale" },
            { value: 2, suffix: "%", label: "Guadagno per Correzione" },
          ].map((s) => (
            <div key={s.label} className="md:px-10 first:pl-0 last:pr-0">
              <StatCounterDark value={s.value} suffix={s.suffix} label={s.label} />
            </div>
          ))}
        </div>
      </div>
    </section>
  );
}

function StatCounterDark({ value, suffix, label }: { value: number; suffix: string; label: string }) {
  const { ref, inView } = useInView();
  const count = useCounter(value, 1600, inView);
  return (
    <div ref={ref}>
      <div className="font-display text-5xl text-[#F5F4F0] leading-none">
        {count}{suffix}
      </div>
      <div className="text-xs text-[#888] mt-2 uppercase tracking-widest font-medium">{label}</div>
    </div>
  );
}

// ── Features Section ───────────────────────────────────────────────────────
function Features() {
  const features = [
    {
      num: "01",
      title: "Analisi Statica Profonda",
      subtitle: "AST + Euristiche",
      desc: "Parsing strutturale tramite Abstract Syntax Tree. Calcolo della complessità ciclomatica con Radon (Python) e conteggio nodi (Java). Rilevamento preciso di cicli annidati, ricorsioni profonde e inefficienze di memoria.",
      tags: ["Python", "Java", "TypeScript"],
    },
    {
      num: "02",
      title: "Monitoraggio Runtime",
      subtitle: "Validazione Empirica",
      desc: "Esecuzione controllata in sottoprocessi isolati con timeout di sicurezza. Campionamento psutil di CPU (%) e RAM (RSS) per catturare picchi di carico. Serie temporali per confrontare performance pre e post refactoring.",
      tags: ["CPU", "RAM", "Profiling"],
    },
    {
      num: "03",
      title: "Stima Economica Azure",
      subtitle: "ROI Quantificabile",
      desc: "Traduzione delle inefficienze tecniche in metriche finanziarie. Calcolo basato su Azure VM Standard D2s v3 (0,09 €/h). Ogni correzione contribuisce al 2% di efficienza, fino al 50% di risparmio massimo.",
      tags: ["Azure", "ROI", "Cost Saving"],
    },
    {
      num: "04",
      title: "Refactoring Azionabile",
      subtitle: "Suggerimenti Precisi",
      desc: "Indicazioni specifiche per ogni pattern di inefficienza: sostituzione di concatenazioni stringa in loop, ottimizzazione di cicli annidati, conversione di ricorsioni profonde in iterazioni, uso di generatori Python.",
      tags: ["Refactoring", "Best Practice"],
    },
  ];

  return (
    <section id="features" className="py-24 bg-[#F5F4F0]">
      <div className="container">
        {/* Section header */}
        <div className="flex items-start gap-8 mb-16">
          <div className="hidden lg:block">
            <div className="font-display text-[9rem] leading-none text-[#1A1A1A]/[0.05] select-none">
              FEAT
            </div>
          </div>
          <div className="flex-1">
            <div className="flex items-center gap-3 mb-4">
              <div className="w-8 h-[3px] bg-[#D4380D]" />
              <span className="text-xs font-semibold uppercase tracking-[0.2em] text-[#D4380D]">Funzionalità</span>
            </div>
            <h2 className="font-display text-[clamp(2.5rem,5vw,4rem)] text-[#1A1A1A] leading-none mb-4">
              UN SISTEMA UNIFICATO<br />PER L'ANALISI COMPLETA
            </h2>
            <p className="text-[#555] max-w-xl leading-relaxed">
              Dalla scansione del codice sorgente alla stima del risparmio economico annuo su Azure,
              tutto in un unico strumento integrato.
            </p>
          </div>
        </div>

        <hr className="rule-thick mb-16" />

        {/* Feature grid */}
        <div className="grid md:grid-cols-2 gap-0">
          {features.map((f, i) => (
            <div
              key={f.num}
              className={`p-8 border-[#D0CFC9] ${
                i % 2 === 0 ? "border-r" : ""
              } ${i < 2 ? "border-b" : ""}`}
            >
              <div className="flex items-start gap-6">
                <div className="font-display text-5xl text-[#D4380D]/30 leading-none shrink-0 w-16">
                  {f.num}
                </div>
                <div>
                  <div className="text-xs font-semibold uppercase tracking-widest text-[#003A8C] mb-1">
                    {f.subtitle}
                  </div>
                  <h3 className="font-display text-2xl text-[#1A1A1A] mb-3">{f.title}</h3>
                  <p className="text-sm text-[#555] leading-relaxed mb-4">{f.desc}</p>
                  <div className="flex flex-wrap gap-2">
                    {f.tags.map((t) => (
                      <span
                        key={t}
                        className="text-xs font-medium bg-[#1A1A1A]/[0.07] text-[#1A1A1A] px-2 py-1 uppercase tracking-wider"
                      >
                        {t}
                      </span>
                    ))}
                  </div>
                </div>
              </div>
            </div>
          ))}
        </div>
      </div>
    </section>
  );
}

// ── How It Works ───────────────────────────────────────────────────────────
function HowItWorks() {
  const steps = [
    { n: "1", title: "Carica il Codice", desc: "File singolo, snippet incollato o intera directory di progetto. Auto-rilevazione del linguaggio (Python, Java, TypeScript)." },
    { n: "2", title: "Analisi Statica", desc: "Parsing AST e analisi euristica per identificare pattern di inefficienza, complessità ciclomatica e strutture dati problematiche." },
    { n: "3", title: "Esecuzione Runtime", desc: "Il codice viene eseguito in un sottoprocesso isolato con campionamento continuo di CPU e RAM tramite psutil." },
    { n: "4", title: "Report e Stima", desc: "Report dettagliato con severità per ogni criticità, suggerimenti di refactoring e calcolo del risparmio annuo su Azure." },
  ];

  return (
    <section id="how-it-works" className="py-24 bg-[#1A1A1A]">
      <div className="container">
        <div className="flex items-center gap-3 mb-4">
          <div className="w-8 h-[3px] bg-[#D4380D]" />
          <span className="text-xs font-semibold uppercase tracking-[0.2em] text-[#D4380D]">Come Funziona</span>
        </div>
        <h2 className="font-display text-[clamp(2.5rem,5vw,4rem)] text-[#F5F4F0] leading-none mb-16">
          QUATTRO PASSI VERSO<br />IL CODICE OTTIMIZZATO
        </h2>

        <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-0 border border-[#333]">
          {steps.map((s, i) => (
            <div
              key={s.n}
              className={`p-8 border-[#333] ${i < 3 ? "border-r" : ""}`}
            >
              <div className="font-display text-[5rem] text-[#D4380D]/20 leading-none mb-4">{s.n}</div>
              <h3 className="font-display text-xl text-[#F5F4F0] mb-3">{s.title}</h3>
              <p className="text-sm text-[#999] leading-relaxed">{s.desc}</p>
            </div>
          ))}
        </div>

        {/* Visual */}
        <div className="mt-16 relative overflow-hidden">
          <img
            src="https://d2xsxph8kpxj0f.cloudfront.net/310519663455238999/VxRZDeE7HcGjoa9uRc77vg/code-analysis-visual-QqsZfj8K8JEFAEdMb3jzq2.png"
            alt="Visualizzazione analisi codice"
            className="w-full max-h-80 object-cover object-top opacity-70"
          />
          <div className="absolute inset-0 bg-gradient-to-t from-[#1A1A1A] via-transparent to-transparent" />
        </div>
      </div>
    </section>
  );
}

// ── Savings Section ────────────────────────────────────────────────────────
function Savings() {
  const { ref, inView } = useInView(0.1);

  return (
    <section id="savings" className="py-24 bg-[#F5F4F0]">
      <div className="container">
        <div className="grid lg:grid-cols-2 gap-16 items-center">
          {/* Left: text */}
          <div>
            <div className="flex items-center gap-3 mb-4">
              <div className="w-8 h-[3px] bg-[#D4380D]" />
              <span className="text-xs font-semibold uppercase tracking-[0.2em] text-[#D4380D]">Impatto Finanziario</span>
            </div>
            <h2 className="font-display text-[clamp(2.5rem,5vw,4rem)] text-[#1A1A1A] leading-none mb-6">
              RISPARMIO ECONOMICO<br />QUANTIFICABILE
            </h2>
            <p className="text-[#555] leading-relaxed mb-8">
              Il modello di calcolo si basa su <strong>Azure VM Standard D2s v3</strong> (2 vCPU, 8 GB RAM)
              con costo orario di ~0,09 €, operatività 24/7 (8.760 ore/anno).
              Ogni inefficienza corretta contribuisce al <strong>2% di efficienza</strong>, fino a un massimo del 50%.
            </p>

            <div className="space-y-4" ref={ref}>
              <StatCounter value={50} suffix="%" label="Risparmio massimo raggiungibile" />
              <StatCounter value={394} suffix="€" label="Risparmio annuo massimo (VM D2s v3)" />
              <StatCounter value={25} suffix="" label="Correzioni per il risparmio massimo" />
            </div>

            <div className="mt-8 p-4 border-l-4 border-[#003A8C] bg-[#003A8C]/[0.04]">
              <p className="text-sm text-[#444] leading-relaxed">
                <strong>Formula:</strong> Risparmio Annuo = Costo Azure × 8.760h × Guadagno di Efficienza
              </p>
            </div>
          </div>

          {/* Right: image */}
          <div className="relative">
            <img
              src="https://d2xsxph8kpxj0f.cloudfront.net/310519663455238999/VxRZDeE7HcGjoa9uRc77vg/azure-cost-visual-mgdDgAqY4mXkHfyVZhNwAz.png"
              alt="Stima risparmio Azure"
              className="w-full object-contain"
            />
            <div className="absolute top-4 right-4 bg-[#D4380D] text-[#F5F4F0] px-4 py-2">
              <div className="font-display text-2xl">AZURE</div>
              <div className="text-xs uppercase tracking-widest">Cost Model</div>
            </div>
          </div>
        </div>
      </div>
    </section>
  );
}

// ── Comparison Table ───────────────────────────────────────────────────────
function ComparisonTable() {
  const features = [
    "Analisi Statica Multi-linguaggio",
    "Monitoraggio Runtime (CPU/RAM)",
    "Stima Costi Cloud",
    "Suggerimenti di Refactoring",
    "Supporto Python",
    "Supporto Java",
    "Supporto TypeScript/Angular",
    "Integrazione CI/CD",
    "Interfaccia Web",
    "Open Source / Self-hosted",
  ];

  const products = [
    {
      name: "CodePerf",
      subtitle: "Questa soluzione",
      highlight: true,
      values: [true, true, true, true, true, true, true, true, true, true],
    },
    {
      name: "SonarQube",
      subtitle: "Analisi statica",
      highlight: false,
      values: [true, false, false, true, true, true, true, true, true, false],
    },
    {
      name: "Codacy",
      subtitle: "Code quality",
      highlight: false,
      values: [true, false, false, true, true, true, true, true, true, false],
    },
    {
      name: "Datadog Profiler",
      subtitle: "Runtime profiling",
      highlight: false,
      values: [false, true, true, false, true, true, true, true, true, false],
    },
    {
      name: "Amazon CodeGuru",
      subtitle: "AI-powered",
      highlight: false,
      values: [true, true, true, true, true, false, false, true, true, false],
    },
  ];

  return (
    <section id="compare" className="py-24 bg-[#F5F4F0]">
      <div className="container">
        <div className="flex items-center gap-3 mb-4">
          <div className="w-8 h-[3px] bg-[#D4380D]" />
          <span className="text-xs font-semibold uppercase tracking-[0.2em] text-[#D4380D]">Confronto</span>
        </div>
        <h2 className="font-display text-[clamp(2.5rem,5vw,4rem)] text-[#1A1A1A] leading-none mb-4">
          CONFRONTO CON<br />I PRODOTTI SIMILI
        </h2>
        <p className="text-[#555] max-w-xl mb-12 leading-relaxed">
          L'unico strumento che integra analisi statica, monitoraggio runtime e stima economica
          in un'unica soluzione self-hosted.
        </p>

        <hr className="rule-thick mb-0" />

        {/* Table */}
        <div className="overflow-x-auto">
          <table className="w-full min-w-[800px] text-sm">
            <thead>
              <tr className="border-b-2 border-[#1A1A1A]">
                <th className="text-left py-4 pr-6 font-semibold text-[#1A1A1A] uppercase tracking-wider text-xs w-56">
                  Funzionalità
                </th>
                {products.map((p) => (
                  <th
                    key={p.name}
                    className={`py-4 px-4 text-center font-display text-lg tracking-wider ${
                      p.highlight
                        ? "bg-[#003A8C] text-[#F5F4F0]"
                        : "text-[#1A1A1A]"
                    }`}
                  >
                    <div>{p.name}</div>
                    <div className={`text-xs font-sans font-normal tracking-normal normal-case ${p.highlight ? "text-[#F5F4F0]/70" : "text-[#888]"}`}>
                      {p.subtitle}
                    </div>
                  </th>
                ))}
              </tr>
            </thead>
            <tbody>
              {features.map((feat, fi) => (
                <tr
                  key={feat}
                  className={`border-b border-[#D0CFC9] ${fi % 2 === 0 ? "bg-[#F5F4F0]" : "bg-[#EEEDE9]"}`}
                >
                  <td className="py-3 pr-6 text-[#333] font-medium">{feat}</td>
                  {products.map((p) => (
                    <td
                      key={p.name}
                      className={`py-3 px-4 text-center ${p.highlight ? "bg-[#003A8C]/[0.06]" : ""}`}
                    >
                      {p.values[fi] ? (
                        <span className={`inline-flex items-center justify-center w-6 h-6 ${p.highlight ? "bg-[#003A8C] text-[#F5F4F0]" : "bg-[#1A1A1A]/10 text-[#1A1A1A]"}`}>
                          ✓
                        </span>
                      ) : (
                        <span className="inline-flex items-center justify-center w-6 h-6 text-[#CCC]">
                          —
                        </span>
                      )}
                    </td>
                  ))}
                </tr>
              ))}
            </tbody>
          </table>
        </div>

        {/* Legend */}
        <div className="mt-6 flex items-center gap-6 text-xs text-[#888]">
          <div className="flex items-center gap-2">
            <span className="inline-flex items-center justify-center w-5 h-5 bg-[#003A8C] text-[#F5F4F0] text-xs">✓</span>
            <span>Supportato (CodePerf)</span>
          </div>
          <div className="flex items-center gap-2">
            <span className="inline-flex items-center justify-center w-5 h-5 bg-[#1A1A1A]/10 text-[#1A1A1A] text-xs">✓</span>
            <span>Supportato (altri)</span>
          </div>
          <div className="flex items-center gap-2">
            <span className="inline-flex items-center justify-center w-5 h-5 text-[#CCC] text-xs">—</span>
            <span>Non supportato</span>
          </div>
        </div>
      </div>
    </section>
  );
}

// ── Languages Section ──────────────────────────────────────────────────────
function Languages() {
  const langs = [
    {
      name: "Python",
      color: "#003A8C",
      features: ["Radon per complessità ciclomatica", "Rilevamento cicli annidati", "Analisi generatori e liste", "Profiling psutil nativo"],
    },
    {
      name: "Java",
      color: "#D4380D",
      features: ["Conteggio nodi AST", "Rilevamento ricorsioni profonde", "Analisi strutture dati", "Complessità metodi"],
    },
    {
      name: "TypeScript",
      color: "#1A1A1A",
      features: ["Pattern Angular specifici", "Concatenazioni in loop", "Analisi componenti", "Ottimizzazione RxJS"],
    },
  ];

  return (
    <section className="py-24 bg-[#EEEDE9]">
      <div className="container">
        <div className="flex items-center gap-3 mb-4">
          <div className="w-8 h-[3px] bg-[#D4380D]" />
          <span className="text-xs font-semibold uppercase tracking-[0.2em] text-[#D4380D]">Linguaggi</span>
        </div>
        <h2 className="font-display text-[clamp(2.5rem,5vw,4rem)] text-[#1A1A1A] leading-none mb-16">
          SUPPORTO NATIVO<br />PER TRE LINGUAGGI
        </h2>

        <div className="grid md:grid-cols-3 gap-0 border border-[#D0CFC9]">
          {langs.map((l, i) => (
            <div
              key={l.name}
              className={`p-8 ${i < 2 ? "border-r border-[#D0CFC9]" : ""}`}
            >
              <div
                className="font-display text-5xl mb-6 pb-4 border-b-4"
                style={{ color: l.color, borderColor: l.color }}
              >
                {l.name}
              </div>
              <ul className="space-y-3">
                {l.features.map((f) => (
                  <li key={f} className="flex items-start gap-3 text-sm text-[#444]">
                    <div className="w-1.5 h-1.5 rounded-full mt-1.5 shrink-0" style={{ backgroundColor: l.color }} />
                    {f}
                  </li>
                ))}
              </ul>
            </div>
          ))}
        </div>
      </div>
    </section>
  );
}

// ── CTA / Contact Section ──────────────────────────────────────────────────
function CTA() {
  return (
    <section id="contact" className="py-24 bg-[#003A8C]">
      <div className="container">
        <div className="grid lg:grid-cols-2 gap-16 items-center">
          <div>
            <div className="flex items-center gap-3 mb-4">
              <div className="w-8 h-[3px] bg-[#D4380D]" />
              <span className="text-xs font-semibold uppercase tracking-[0.2em] text-[#D4380D]">Inizia Ora</span>
            </div>
            <h2 className="font-display text-[clamp(2.5rem,5vw,4rem)] text-[#F5F4F0] leading-none mb-6">
              OTTIMIZZA IL TUO<br />CODICE OGGI
            </h2>
            <p className="text-[#B8C8E8] leading-relaxed mb-8">
              Richiedi una demo personalizzata o contattaci per scoprire come integrare
              l'analizzatore nel tuo workflow di sviluppo e CI/CD pipeline.
            </p>
            <div className="flex flex-col gap-3 text-sm text-[#B8C8E8]">
              <div className="flex items-center gap-3">
                <div className="w-2 h-2 bg-[#D4380D]" />
                <span>Analisi immediata senza configurazione</span>
              </div>
              <div className="flex items-center gap-3">
                <div className="w-2 h-2 bg-[#D4380D]" />
                <span>Integrazione con pipeline CI/CD esistenti</span>
              </div>
              <div className="flex items-center gap-3">
                <div className="w-2 h-2 bg-[#D4380D]" />
                <span>Report esportabili in formato JSON e HTML</span>
              </div>
            </div>
          </div>

          {/* Contact form */}
          <div className="bg-[#F5F4F0] p-8">
            <h3 className="font-display text-2xl text-[#1A1A1A] mb-6">RICHIEDI UNA DEMO</h3>
            <div className="space-y-4">
              <div>
                <label className="block text-xs font-semibold uppercase tracking-widest text-[#555] mb-1">
                  Nome e Cognome
                </label>
                <input
                  type="text"
                  placeholder="Mario Rossi"
                  className="w-full border border-[#D0CFC9] bg-white px-4 py-3 text-sm text-[#1A1A1A] focus:outline-none focus:border-[#003A8C]"
                />
              </div>
              <div>
                <label className="block text-xs font-semibold uppercase tracking-widest text-[#555] mb-1">
                  Email Aziendale
                </label>
                <input
                  type="email"
                  placeholder="mario@azienda.it"
                  className="w-full border border-[#D0CFC9] bg-white px-4 py-3 text-sm text-[#1A1A1A] focus:outline-none focus:border-[#003A8C]"
                />
              </div>
              <div>
                <label className="block text-xs font-semibold uppercase tracking-widest text-[#555] mb-1">
                  Linguaggio Principale
                </label>
                <select className="w-full border border-[#D0CFC9] bg-white px-4 py-3 text-sm text-[#1A1A1A] focus:outline-none focus:border-[#003A8C]">
                  <option value="">Seleziona...</option>
                  <option>Python</option>
                  <option>Java</option>
                  <option>TypeScript</option>
                  <option>Multi-linguaggio</option>
                </select>
              </div>
              <button
                className="w-full bg-[#D4380D] text-[#F5F4F0] py-4 font-semibold text-sm uppercase tracking-widest hover:bg-[#b82e08] transition-colors"
                onClick={() => alert("Grazie! Ti contatteremo presto.")}
              >
                Invia Richiesta
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>
  );
}

// ── Footer ─────────────────────────────────────────────────────────────────
function Footer() {
  return (
    <footer className="bg-[#1A1A1A] py-10">
      <div className="container flex flex-col md:flex-row items-center justify-between gap-4">
        <div className="font-display text-2xl text-[#F5F4F0] tracking-wider">
          CODE<span className="text-[#D4380D]">PERF</span>
        </div>
        <p className="text-xs text-[#666] text-center">
          Analizzatore Multi-linguaggio di Performance del Codice · Ottimizzazione e Risparmio Economico su Azure
        </p>
        <div className="flex gap-6 text-xs text-[#666]">
          <a href="#features" className="hover:text-[#F5F4F0] transition-colors">Funzionalità</a>
          <a href="#compare" className="hover:text-[#F5F4F0] transition-colors">Confronto</a>
          <a href="#contact" className="hover:text-[#F5F4F0] transition-colors">Contatti</a>
        </div>
      </div>
    </footer>
  );
}

// ── Main export ────────────────────────────────────────────────────────────
export default function Home() {
  return (
    <div className="min-h-screen">
      <Navbar />
      <Hero />
      <StatsBar />
      <Features />
      <HowItWorks />
      <Savings />
      <ComparisonTable />
      <Languages />
      <CTA />
      <Footer />
    </div>
  );
}
