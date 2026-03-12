import { useState, useEffect, useRef } from "react";

const COLORS = {
  bg: "#0d0f18",
  bgAlt: "#1a1b2e",
  bgPanel: "#16213e",
  green: "#57e89d",
  greenDim: "#3a9e6e",
  greenGlow: "#57e89d44",
  cyan: "#7dcfff",
  purple: "#bb9af7",
  orange: "#ff9e64",
  red: "#f7768e",
  yellow: "#e0af68",
  white: "#c0caf5",
  dim: "#565f89",
  border: "#1f2335",
};

const NvimLogo = ({ size = 80, animate = true }) => {
  const [glow, setGlow] = useState(0);
  useEffect(() => {
    if (!animate) return;
    const t = setInterval(() => setGlow(g => (g + 1) % 100), 50);
    return () => clearInterval(t);
  }, [animate]);
  const glowVal = Math.sin(glow / 15) * 0.5 + 0.5;

  return (
    <svg width={size} height={size} viewBox="0 0 100 100" style={{
      filter: `drop-shadow(0 0 ${8 + glowVal * 16}px ${COLORS.green}) drop-shadow(0 0 ${4 + glowVal * 8}px ${COLORS.greenDim})`,
      transition: "filter 0.1s"
    }}>
      {/* Neovim N logo */}
      <polygon points="12,82 12,18 32,18 60,62 60,18 88,18 88,82 68,82 40,38 40,82" 
        fill="none" stroke={COLORS.green} strokeWidth="6" strokeLinejoin="round" strokeLinecap="round"/>
      <polygon points="12,82 12,18 32,18 60,62 60,18 88,18 88,82 68,82 40,38 40,82" 
        fill={`${COLORS.green}18`}/>
      {/* inner accent lines */}
      <line x1="12" y1="18" x2="12" y2="82" stroke={COLORS.green} strokeWidth="6" strokeLinecap="round"/>
      <line x1="88" y1="18" x2="88" y2="82" stroke={COLORS.green} strokeWidth="6" strokeLinecap="round"/>
    </svg>
  );
};

const TypeWriter = ({ text, speed = 40, color = COLORS.green, onDone, className }) => {
  const [displayed, setDisplayed] = useState("");
  const [idx, setIdx] = useState(0);
  useEffect(() => {
    if (idx < text.length) {
      const t = setTimeout(() => { setDisplayed(d => d + text[idx]); setIdx(i => i + 1); }, speed);
      return () => clearTimeout(t);
    } else if (onDone) onDone();
  }, [idx, text, speed]);
  return (
    <span className={className} style={{ color, fontFamily: "'JetBrains Mono', 'Fira Code', monospace" }}>
      {displayed}
      {idx < text.length && <span style={{ animation: "blink 1s infinite", color: COLORS.green }}>█</span>}
    </span>
  );
};

const TerminalLine = ({ prefix, text, prefixColor = COLORS.green, delay = 0 }) => {
  const [visible, setVisible] = useState(false);
  useEffect(() => { const t = setTimeout(() => setVisible(true), delay); return () => clearTimeout(t); }, [delay]);
  if (!visible) return null;
  return (
    <div style={{ display: "flex", gap: 8, marginBottom: 4, fontFamily: "monospace", fontSize: 13 }}>
      <span style={{ color: prefixColor, flexShrink: 0 }}>{prefix}</span>
      <span style={{ color: COLORS.white }}>{text}</span>
    </div>
  );
};

const GlowBar = ({ label, value, color = COLORS.green, delay = 0 }) => {
  const [width, setWidth] = useState(0);
  useEffect(() => { const t = setTimeout(() => setWidth(value), delay + 300); return () => clearTimeout(t); }, []);
  return (
    <div style={{ marginBottom: 10 }}>
      <div style={{ display: "flex", justifyContent: "space-between", marginBottom: 4, fontSize: 12, fontFamily: "monospace" }}>
        <span style={{ color: COLORS.dim }}>{label}</span>
        <span style={{ color }}>{value}%</span>
      </div>
      <div style={{ height: 6, background: COLORS.border, borderRadius: 3, overflow: "hidden" }}>
        <div style={{
          height: "100%", width: `${width}%`, borderRadius: 3,
          background: `linear-gradient(90deg, ${color}99, ${color})`,
          boxShadow: `0 0 8px ${color}`,
          transition: "width 1.2s cubic-bezier(0.16,1,0.3,1)"
        }} />
      </div>
    </div>
  );
};

const ProjectCard = ({ rank, name, desc, stack, stars, delay = 0 }) => {
  const [visible, setVisible] = useState(false);
  const [hovered, setHovered] = useState(false);
  useEffect(() => { const t = setTimeout(() => setVisible(true), delay); return () => clearTimeout(t); }, []);
  const rankColor = { S: COLORS.yellow, A: COLORS.green, B: COLORS.cyan }[rank] || COLORS.dim;
  return (
    <div style={{
      opacity: visible ? 1 : 0, transform: visible ? "translateY(0)" : "translateY(20px)",
      transition: "all 0.6s cubic-bezier(0.16,1,0.3,1)",
      background: hovered ? `${COLORS.bgPanel}` : COLORS.bgAlt,
      border: `1px solid ${hovered ? COLORS.green + "66" : COLORS.border}`,
      borderRadius: 8, padding: "16px 20px", marginBottom: 10, cursor: "pointer",
      boxShadow: hovered ? `0 0 24px ${COLORS.greenGlow}, inset 0 0 24px ${COLORS.greenGlow}` : "none",
      transform: visible ? (hovered ? "translateY(-2px)" : "translateY(0)") : "translateY(20px)",
    }}
      onMouseEnter={() => setHovered(true)} onMouseLeave={() => setHovered(false)}
    >
      <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 8 }}>
        <span style={{ fontFamily: "monospace", fontWeight: "bold", fontSize: 13, color: rankColor,
          border: `1px solid ${rankColor}44`, borderRadius: 4, padding: "2px 8px" }}>{rank}</span>
        <span style={{ fontFamily: "monospace", fontWeight: "bold", fontSize: 15, color: COLORS.white }}>{name}</span>
        <span style={{ marginLeft: "auto", fontSize: 12, color: COLORS.yellow, fontFamily: "monospace" }}>⭐ {stars}</span>
      </div>
      <p style={{ fontSize: 13, color: COLORS.dim, margin: "0 0 10px", fontFamily: "monospace", lineHeight: 1.5 }}>{desc}</p>
      <div style={{ display: "flex", gap: 6, flexWrap: "wrap" }}>
        {stack.map(t => (
          <span key={t} style={{ fontSize: 11, fontFamily: "monospace", color: COLORS.cyan,
            background: `${COLORS.cyan}15`, border: `1px solid ${COLORS.cyan}33`,
            borderRadius: 4, padding: "2px 8px" }}>{t}</span>
        ))}
      </div>
    </div>
  );
};

const FloatingParticle = ({ style }) => (
  <div style={{
    position: "absolute", width: 2, height: 2, borderRadius: "50%",
    background: COLORS.green, opacity: 0.4,
    animation: `float ${3 + Math.random() * 4}s ease-in-out infinite`,
    animationDelay: `${Math.random() * 3}s`, ...style
  }} />
);

const TAB_DATA = ["about", "skills", "projects", "watching", "contact"];

export default function App() {
  const [activeTab, setActiveTab] = useState("about");
  const [headerDone, setHeaderDone] = useState(false);
  const [cmdVisible, setCmdVisible] = useState(false);
  const [currentTime, setCurrentTime] = useState(new Date());

  useEffect(() => {
    const t = setInterval(() => setCurrentTime(new Date()), 1000);
    return () => clearInterval(t);
  }, []);

  useEffect(() => {
    if (headerDone) setTimeout(() => setCmdVisible(true), 400);
  }, [headerDone]);

  const timeStr = currentTime.toLocaleTimeString("en-US", { hour12: false });

  return (
    <div style={{ minHeight: "100vh", background: COLORS.bg, color: COLORS.white, fontFamily: "monospace" }}>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&display=swap');
        @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }
        @keyframes float { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-12px)} }
        @keyframes scanline { 0%{transform:translateY(-100%)} 100%{transform:translateY(100vh)} }
        @keyframes pulse { 0%,100%{opacity:0.6} 50%{opacity:1} }
        @keyframes slideIn { from{opacity:0;transform:translateX(-20px)} to{opacity:1;transform:translateX(0)} }
        ::-webkit-scrollbar{width:4px} ::-webkit-scrollbar-track{background:#0d0f18}
        ::-webkit-scrollbar-thumb{background:#57e89d44;border-radius:2px}
        * { box-sizing: border-box; }
      `}</style>

      {/* Scanline overlay */}
      <div style={{ position: "fixed", inset: 0, pointerEvents: "none", zIndex: 100, overflow: "hidden", opacity: 0.03 }}>
        <div style={{ width: "100%", height: 2, background: COLORS.green,
          animation: "scanline 8s linear infinite" }} />
      </div>

      {/* Floating particles */}
      <div style={{ position: "fixed", inset: 0, pointerEvents
