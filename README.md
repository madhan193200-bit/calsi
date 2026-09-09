# calsi
# https://neon-scientific-calculator--madhan193200.replit.app
Calsi Web Source Code
====================

This file combines the editable website source files.



===== FILE: artifacts/neon-calculator/index.html =====
====================================

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1" />
    <title>Calsi — Scientific Calculator</title>
    <meta name="description" content="Calsi is an offline-first scientific calculator and conversion toolkit." />
    <meta name="robots" content="index, follow" />
    <meta property="og:title" content="Calsi — Scientific Calculator" />
    <meta property="og:description" content="Calsi is an offline-first scientific calculator and conversion toolkit." />
    <meta property="og:type" content="website" />
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="Calsi — Scientific Calculator" />
    <meta name="twitter:description" content="Calsi is an offline-first scientific calculator and conversion toolkit." />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>


===== FILE: artifacts/neon-calculator/package.json =====
======================================

{
  "name": "@workspace/neon-calculator",
  "version": "0.0.0",
  "private": true,
  "type": "module",
  "scripts": {
    "dev": "vite --config vite.config.ts --host 0.0.0.0",
    "build": "vite build --config vite.config.ts",
    "serve": "vite preview --config vite.config.ts --host 0.0.0.0",
    "typecheck": "tsc -p tsconfig.json --noEmit"
  },
  "devDependencies": {
    "@hookform/resolvers": "^3.10.0",
    "@radix-ui/react-accordion": "^1.2.4",
    "@radix-ui/react-alert-dialog": "^1.1.7",
    "@radix-ui/react-aspect-ratio": "^1.1.3",
    "@radix-ui/react-avatar": "^1.1.4",
    "@radix-ui/react-checkbox": "^1.1.5",
    "@radix-ui/react-collapsible": "^1.1.4",
    "@radix-ui/react-context-menu": "^2.2.7",
    "@radix-ui/react-dialog": "^1.1.7",
    "@radix-ui/react-dropdown-menu": "^2.1.7",
    "@radix-ui/react-hover-card": "^1.1.7",
    "@radix-ui/react-label": "^2.1.3",
    "@radix-ui/react-menubar": "^1.1.7",
    "@radix-ui/react-navigation-menu": "^1.2.6",
    "@radix-ui/react-popover": "^1.1.7",
    "@radix-ui/react-progress": "^1.1.3",
    "@radix-ui/react-radio-group": "^1.2.4",
    "@radix-ui/react-scroll-area": "^1.2.4",
    "@radix-ui/react-select": "^2.1.7",
    "@radix-ui/react-separator": "^1.1.3",
    "@radix-ui/react-slider": "^1.2.4",
    "@radix-ui/react-slot": "^1.2.0",
    "@radix-ui/react-switch": "^1.1.4",
    "@radix-ui/react-tabs": "^1.1.4",
    "@radix-ui/react-toast": "^1.2.7",
    "@radix-ui/react-toggle": "^1.1.3",
    "@radix-ui/react-toggle-group": "^1.1.3",
    "@radix-ui/react-tooltip": "^1.2.0",
    "@replit/vite-plugin-cartographer": "catalog:",
    "@replit/vite-plugin-dev-banner": "catalog:",
    "@replit/vite-plugin-runtime-error-modal": "catalog:",
    "@tailwindcss/typography": "^0.5.15",
    "@tailwindcss/vite": "catalog:",
    "@tanstack/react-query": "catalog:",
    "@types/node": "catalog:",
    "@types/react": "catalog:",
    "@types/react-dom": "catalog:",
    "@vitejs/plugin-react": "catalog:",
    "@workspace/api-client-react": "workspace:*",
    "class-variance-authority": "catalog:",
    "clsx": "catalog:",
    "cmdk": "^1.1.1",
    "date-fns": "^3.6.0",
    "embla-carousel-react": "^8.6.0",
    "framer-motion": "catalog:",
    "input-otp": "^1.4.2",
    "lucide-react": "catalog:",
    "next-themes": "^0.4.6",
    "react": "catalog:",
    "react-day-picker": "^9.11.1",
    "react-dom": "catalog:",
    "react-hook-form": "^7.55.0",
    "react-icons": "^5.4.0",
    "react-resizable-panels": "^2.1.7",
    "recharts": "^2.15.2",
    "sonner": "^2.0.7",
    "tailwind-merge": "catalog:",
    "tailwindcss": "catalog:",
    "tw-animate-css": "^1.4.0",
    "vaul": "^1.1.2",
    "vite": "catalog:",
    "wouter": "^3.3.5",
    "zod": "catalog:"
  }
}


===== FILE: artifacts/neon-calculator/tsconfig.json =====
=======================================

{
  "extends": "../../tsconfig.base.json",
  "include": ["src/**/*"],
  "exclude": ["node_modules", "build", "dist", "**/*.test.ts"],
  "compilerOptions": {
    "noEmit": true,
    "jsx": "preserve",
    "lib": ["esnext", "dom", "dom.iterable"],
    "resolveJsonModule": true,
    "allowImportingTsExtensions": true,
    "moduleResolution": "bundler",
    "types": ["node", "vite/client"],
    "paths": {
      "@/*": ["./src/*"]
    }
  },
  "references": [
    {
      "path": "../../lib/api-client-react"
    }
  ]
}


===== FILE: artifacts/neon-calculator/vite.config.ts =====
========================================

import path from 'path';
import react from '@vitejs/plugin-react';
import tailwindcss from '@tailwindcss/vite';
import { defineConfig } from 'vite';

import runtimeErrorOverlay from '@replit/vite-plugin-runtime-error-modal';

const rawPort = process.env.PORT;

if (!rawPort) {
  throw new Error(
    'PORT environment variable is required but was not provided.',
  );
}

const port = Number(rawPort);

if (Number.isNaN(port) || port <= 0) {
  throw new Error(`Invalid PORT value: "${rawPort}"`);
}

const basePath = process.env.BASE_PATH;

if (!basePath) {
  throw new Error(
    'BASE_PATH environment variable is required but was not provided.',
  );
}

export default defineConfig({
  base: basePath,
  plugins: [
    react(),
    tailwindcss(),
    runtimeErrorOverlay(),
    ...(process.env.NODE_ENV !== 'production' &&
    process.env.REPL_ID !== undefined
      ? [
          await import('@replit/vite-plugin-cartographer').then((m) =>
            m.cartographer({
              root: path.resolve(import.meta.dirname, '..'),
            }),
          ),
          await import('@replit/vite-plugin-dev-banner').then((m) =>
            m.devBanner(),
          ),
        ]
      : []),
  ],
  resolve: {
    alias: {
      '@': path.resolve(import.meta.dirname, 'src'),
      '@assets': path.resolve(
        import.meta.dirname,
        '..',
        '..',
        'attached_assets',
      ),
    },
    dedupe: ['react', 'react-dom'],
  },
  root: path.resolve(import.meta.dirname),
  build: {
    outDir: path.resolve(import.meta.dirname, 'dist/public'),
    emptyOutDir: true,
  },
  server: {
    port,
    strictPort: true,
    host: '0.0.0.0',
    allowedHosts: true,
    fs: {
      strict: true,
    },
  },
  preview: {
    port,
    host: '0.0.0.0',
    allowedHosts: true,
  },
});


===== FILE: artifacts/neon-calculator/src/main.tsx =====
======================================

import { createRoot } from 'react-dom/client';

import App from './App';
import { ErrorBoundary } from '@/components/error-boundary';

import './index.css';

createRoot(document.getElementById('root')!, {
  // Keeps caught errors off reportError(), which would raise the dev overlay.
  onCaughtError: (error, errorInfo) => {
    console.error(error, errorInfo.componentStack);
  },
}).render(
  <ErrorBoundary>
    <App />
  </ErrorBoundary>,
);


===== FILE: artifacts/neon-calculator/src/App.tsx =====
=====================================

import { useEffect, useMemo, useState, type ReactNode } from 'react';
import {
  ArrowRightLeft, Calculator, Check, Clock3, Copy, Delete,
  History, Keyboard, MoreHorizontal,
  RotateCcw, Ruler, Search, Sparkles, Trash2, X, Zap,
} from 'lucide-react';

type AngleMode = 'DEG' | 'RAD' | 'GRAD';
type Category = 'Currency' | 'Length' | 'Mass' | 'Area' | 'Time' | 'Data' | 'Volume' | 'Speed' | 'Temperature';
type AccentTheme = 'cyan' | 'violet' | 'lime' | 'magenta';
type ExtraTool = 'Finance' | 'Tip split' | 'Percentage' | 'Discount' | 'Date' | 'Numeral system' | 'BMI' | 'GST' | 'Circle lab';
type HistoryItem = { id: string; expression: string; result: string; timestamp: number; mode: AngleMode };

const HISTORY_KEY = 'neon-scientific-history';
const PREFS_KEY = 'neon-scientific-preferences';
const THEME_KEY = 'neon-scientific-accent';

const constants = [
  { label: 'π', value: 'π', detail: '3.14159…' },
  { label: 'e', value: 'e', detail: '2.71828…' },
  { label: 'φ', value: '1.6180339887', detail: 'golden ratio' },
  { label: 'c', value: '299792458', detail: 'speed of light' },
];

const converterData: Record<Category, { units: string[]; convert: (v: number, from: string, to: string) => number }> = {
  Currency: {
    units: ['USD', 'INR', 'EUR', 'GBP', 'JPY'],
    convert: (v, from, to) => {
      const base: Record<string, number> = { USD: 1, INR: 83.1, EUR: .92, GBP: .78, JPY: 157 };
      return v * base[from] / base[to];
    },
  },
  Length: {
    units: ['Meters', 'Kilometers', 'Feet', 'Miles', 'Inches'],
    convert: (v, from, to) => {
      const base: Record<string, number> = { Meters: 1, Kilometers: 1000, Feet: .3048, Miles: 1609.344, Inches: .0254 };
      return v * base[from] / base[to];
    },
  },
  Mass: {
    units: ['Grams', 'Kilograms', 'Pounds', 'Ounces'],
    convert: (v, from, to) => {
      const base: Record<string, number> = { Grams: 1, Kilograms: 1000, Pounds: 453.59237, Ounces: 28.349523125 };
      return v * base[from] / base[to];
    },
  },
  Temperature: {
    units: ['Celsius', 'Fahrenheit', 'Kelvin'],
    convert: (v, from, to) => {
      const c = from === 'Celsius' ? v : from === 'Fahrenheit' ? (v - 32) * 5 / 9 : v - 273.15;
      return to === 'Celsius' ? c : to === 'Fahrenheit' ? c * 9 / 5 + 32 : c + 273.15;
    },
  },
  Area: {
    units: ['Square meters', 'Square feet', 'Acres', 'Hectares'],
    convert: (v, from, to) => {
      const base: Record<string, number> = { 'Square meters': 1, 'Square feet': .092903, Acres: 4046.856, Hectares: 10000 };
      return v * base[from] / base[to];
    },
  },
  Time: {
    units: ['Seconds', 'Minutes', 'Hours', 'Days'],
    convert: (v, from, to) => {
      const base: Record<string, number> = { Seconds: 1, Minutes: 60, Hours: 3600, Days: 86400 };
      return v * base[from] / base[to];
    },
  },
  Data: {
    units: ['Bytes', 'Kilobytes', 'Megabytes', 'Gigabytes'],
    convert: (v, from, to) => {
      const base: Record<string, number> = { Bytes: 1, Kilobytes: 1024, Megabytes: 1048576, Gigabytes: 1073741824 };
      return v * base[from] / base[to];
    },
  },
  Volume: {
    units: ['Liters', 'Milliliters', 'Gallons', 'Cubic feet'],
    convert: (v, from, to) => {
      const base: Record<string, number> = { Liters: 1, Milliliters: .001, Gallons: 3.78541, 'Cubic feet': 28.3168 };
      return v * base[from] / base[to];
    },
  },
  Speed: {
    units: ['Meters/second', 'Kilometers/hour', 'Miles/hour', 'Knots'],
    convert: (v, from, to) => {
      const base: Record<string, number> = { 'Meters/second': 1, 'Kilometers/hour': .277778, 'Miles/hour': .44704, Knots: .514444 };
      return v * base[from] / base[to];
    },
  },
};

function tokenize(input: string): string[] {
  return input
    .replaceAll('×', '*').replaceAll('÷', '/').replaceAll('−', '-').replaceAll('√', 'sqrt')
    .replace(/\s+/g, '').match(/(?:\d+(?:\.\d*)?|\.\d+|[A-Za-z]+|π|[()+\-*/^%!(),])/g) ?? [];
}

function evaluateExpression(input: string, angle: AngleMode): number {
  const tokens = tokenize(input);
  if (!tokens.length) throw new Error('Enter an expression to begin.');
  let position = 0;
  const peek = () => tokens[position];
  const take = () => tokens[position++];
  const toAngle = (v: number) => angle === 'DEG' ? v * Math.PI / 180 : angle === 'GRAD' ? v * Math.PI / 200 : v;
  const fromAngle = (v: number) => angle === 'DEG' ? v * 180 / Math.PI : angle === 'GRAD' ? v * 200 / Math.PI : v;
  const constantsMap: Record<string, number> = { pi: Math.PI, π: Math.PI, e: Math.E, tau: Math.PI * 2 };
  const functions: Record<string, (v: number) => number> = {
    sin: (v) => Math.sin(toAngle(v)), cos: (v) => Math.cos(toAngle(v)), tan: (v) => Math.tan(toAngle(v)),
    asin: (v) => fromAngle(Math.asin(v)), acos: (v) => fromAngle(Math.acos(v)), atan: (v) => fromAngle(Math.atan(v)),
    sqrt: Math.sqrt, cbrt: Math.cbrt, abs: Math.abs, exp: Math.exp, ln: Math.log,
    log: Math.log10, floor: Math.floor, ceil: Math.ceil,
  };
  const factorial = (n: number) => {
    if (n < 0 || !Number.isInteger(n) || n > 170) throw new Error('Factorial needs a whole number from 0 to 170.');
    let result = 1; for (let i = 2; i <= n; i += 1) result *= i; return result;
  };
  const primary = (): number => {
    const token = take();
    if (!token) throw new Error('The expression is incomplete.');
    if (token === '(') { const value = addition(); if (take() !== ')') throw new Error('Close the open parenthesis.'); return value; }
    if (token === '+' || token === '-') { const v = primary(); return token === '-' ? -v : v; }
    if (/^\d|^\./.test(token)) return Number(token);
    const key = token.toLowerCase();
    if (functions[key]) {
      if (peek() === '(') take();
      const value = addition();
      if (peek() === ')') take();
      return functions[key](value);
    }
    if (constantsMap[key] !== undefined) return constantsMap[key];
    throw new Error(`Unknown token “${token}”.`);
  };
  const power = (): number => {
    let value = primary();
    if (peek() === '!') { take(); value = factorial(value); }
    if (peek() === '%') { take(); value /= 100; }
    if (peek() === '^') { take(); value = value ** power(); }
    return value;
  };
  const multiplication = (): number => {
    let value = power();
    while (peek() === '*' || peek() === '/') {
      const operator = take(); const right = power();
      if (operator === '/' && right === 0) throw new Error('Division by zero is undefined.');
      value = operator === '*' ? value * right : value / right;
    }
    return value;
  };
  const addition = (): number => {
    let value = multiplication();
    while (peek() === '+' || peek() === '-') { const operator = take(); const right = multiplication(); value = operator === '+' ? value + right : value - right; }
    return value;
  };
  const result = addition();
  if (position < tokens.length) throw new Error(`Unexpected token “${tokens[position]}”.`);
  if (!Number.isFinite(result)) throw new Error('That result is outside the instrument’s range.');
  return result;
}

function formatNumber(value: number): string {
  if (Object.is(value, -0)) return '0';
  if (Math.abs(value) >= 1e12 || (Math.abs(value) < 1e-8 && value !== 0)) return value.toExponential(8).replace(/\.?0+e/, 'e');
  return Number(value.toPrecision(12)).toLocaleString('en-US', { maximumFractionDigits: 10, useGrouping: false });
}

function safeRead<T>(key: string, fallback: T): T {
  try { const saved = localStorage.getItem(key); return saved ? JSON.parse(saved) as T : fallback; } catch { return fallback; }
}

function App() {
  const [expression, setExpression] = useState('');
  const [result, setResult] = useState('');
  const [error, setError] = useState('');
  const [angleMode, setAngleMode] = useState<AngleMode>(() => safeRead<{ angle: AngleMode }>(PREFS_KEY, { angle: 'DEG' }).angle);
  const [secondMode, setSecondMode] = useState(false);
  const [history, setHistory] = useState<HistoryItem[]>(() => safeRead(HISTORY_KEY, []));
  const [showHistory, setShowHistory] = useState(false);
  const [copied, setCopied] = useState(false);
  const [accentTheme, setAccentTheme] = useState<AccentTheme>(() => safeRead(THEME_KEY, 'cyan'));
  const [category, setCategory] = useState<Category>('Currency');
  const [fromUnit, setFromUnit] = useState('USD');
  const [toUnit, setToUnit] = useState('INR');
  const [convertValue, setConvertValue] = useState('1');
  const [extraTool, setExtraTool] = useState<ExtraTool>('Finance');
  const [billAmount, setBillAmount] = useState('120');
  const [tipPercent, setTipPercent] = useState('18');
  const [peopleCount, setPeopleCount] = useState('2');
  const [circleRadius, setCircleRadius] = useState('5');
  const [dateValue, setDateValue] = useState('2026-01-01');
  const [dateOffset, setDateOffset] = useState('30');

  useEffect(() => { localStorage.setItem(HISTORY_KEY, JSON.stringify(history)); }, [history]);
  useEffect(() => { localStorage.setItem(PREFS_KEY, JSON.stringify({ angle: angleMode })); }, [angleMode]);
  useEffect(() => {
    localStorage.setItem(THEME_KEY, JSON.stringify(accentTheme));
    document.documentElement.dataset.accent = accentTheme;
  }, [accentTheme]);
  useEffect(() => {
    const onKey = (event: KeyboardEvent) => {
      if (event.metaKey || event.ctrlKey || event.altKey) return;
      if (event.key === 'Enter' || event.key === '=') { event.preventDefault(); calculate(); }
      else if (event.key === 'Escape') reset();
      else if (event.key === 'Backspace') { event.preventDefault(); setExpression((v) => v.slice(0, -1)); }
      else if (/^[0-9+\-*/().%^!]$/.test(event.key)) { setExpression((v) => v + event.key); setError(''); }
    };
    window.addEventListener('keydown', onKey); return () => window.removeEventListener('keydown', onKey);
  });

  const units = converterData[category].units;
  const converted = useMemo(() => {
    const value = Number(convertValue);
    if (!Number.isFinite(value)) return '—';
    return formatNumber(converterData[category].convert(value, fromUnit, toUnit));
  }, [category, convertValue, fromUnit, toUnit]);
  const bill = Number(billAmount);
  const tip = Number(tipPercent);
  const people = Math.max(1, Number(peopleCount) || 1);
  const totalWithTip = Number.isFinite(bill) && Number.isFinite(tip) ? bill * (1 + tip / 100) : 0;
  const circle = Number(circleRadius);
  const circleArea = Number.isFinite(circle) ? Math.PI * circle * circle : 0;
  const circleCircumference = Number.isFinite(circle) ? 2 * Math.PI * circle : 0;
  const extraResult = useMemo(() => {
    const a = Number(billAmount); const b = Number(tipPercent); const c = Number(peopleCount);
    if (extraTool === 'Finance') { const interest = a * b / 100; return `Interest ${formatNumber(interest)} · Total ${formatNumber(a + interest)}`; }
    if (extraTool === 'Percentage') return `${formatNumber(a * b / 100)} is ${formatNumber(b)}% of ${formatNumber(a)}`;
    if (extraTool === 'Discount') return `Save ${formatNumber(a * b / 100)} · Pay ${formatNumber(a - a * b / 100)}`;
    if (extraTool === 'Numeral system') { const base = Math.min(36, Math.max(2, Math.round(b || 2))); return Number.isFinite(a) ? `${Math.trunc(a).toString(base).toUpperCase()} (base ${base})` : 'Use a decimal number'; }
    if (extraTool === 'BMI') { const height = b / 100; const bmi = a / (height * height); return Number.isFinite(bmi) ? `${formatNumber(bmi)} · ${bmi < 18.5 ? 'Underweight' : bmi < 25 ? 'Healthy range' : bmi < 30 ? 'Overweight' : 'Obesity range'}` : 'Use kg and cm'; }
    if (extraTool === 'GST') return `GST ${formatNumber(a * b / 100)} · Total ${formatNumber(a + a * b / 100)}`;
    if (extraTool === 'Date') { const date = new Date(dateValue); if (Number.isNaN(date.getTime())) return 'Use YYYY-MM-DD'; date.setDate(date.getDate() + (Number.isFinite(Number(dateOffset)) ? Number(dateOffset) : 0)); return date.toISOString().slice(0, 10); }
    return `Tip ${formatNumber(a * b / 100)} · Total ${formatNumber(totalWithTip)} · Each ${formatNumber(totalWithTip / people)}`;
  }, [billAmount, tipPercent, peopleCount, extraTool, dateValue, dateOffset, totalWithTip, people]);

  function calculate() {
    try {
      const value = evaluateExpression(expression, angleMode);
      const formatted = formatNumber(value);
      setResult(formatted); setError('');
      setHistory((items) => [{ id: `${Date.now()}-${Math.random()}`, expression, result: formatted, timestamp: Date.now(), mode: angleMode }, ...items].slice(0, 100));
    } catch (e) { setError(e instanceof Error ? e.message : 'Unable to evaluate that expression.'); setResult(''); }
  }
  function reset() { setExpression(''); setResult(''); setError(''); }
  function press(value: string) { setExpression((v) => v + value); setError(''); }
  function replay(item: HistoryItem) { setExpression(item.expression); setResult(item.result); setError(''); setShowHistory(false); }
  async function copy(value: string) {
    if (!value) return;
    try { await navigator.clipboard.writeText(value); setCopied(true); setTimeout(() => setCopied(false), 1300); } catch { setError('Clipboard access is unavailable here.'); }
  }
  function changeCategory(next: Category) {
    setCategory(next); const nextUnits = converterData[next].units; setFromUnit(nextUnits[0]); setToUnit(nextUnits[1] ?? nextUnits[0]);
  }
  function handleKey(value: string) {
    if (value === '2nd') { setSecondMode((current) => !current); return; }
    if (value === 'deg') { setAngleMode((current) => current === 'DEG' ? 'RAD' : current === 'RAD' ? 'GRAD' : 'DEG'); return; }
    if (value === '⇄') { document.getElementById('tools')?.scrollIntoView({ behavior: 'smooth' }); return; }
    if (value === 'AC') { reset(); return; }
    if (value === '⌫') { setExpression((current) => current.slice(0, -1)); return; }
    if (value === '1/x') { press(`1/(${expression || result || '1'})`); return; }
    const mapped: Record<string, string> = { sin: secondMode ? 'asin(' : 'sin(', cos: secondMode ? 'acos(' : 'cos(', tan: secondMode ? 'atan(' : 'tan(', 'xʸ': '^', lg: 'log(', ln: 'ln(', '√x': 'sqrt(', 'x!': '!', 'π': 'π', '−': '-', e: 'e' };
    press(mapped[value] || value);
  }

  return (
    <main className="instrument-shell">
      <header className="mx-auto flex max-w-[1440px] items-center justify-between px-5 py-5 sm:px-8 lg:px-12">
        <div className="flex items-center gap-3">
          <div className="relative flex h-10 w-10 items-center justify-center rounded-xl border border-cyan-300/40 bg-cyan-300/10 text-cyan-200 shadow-[0_0_28px_rgba(88,238,242,.12)]">
            <Sparkles size={19} /><span className="pulse-dot absolute -right-1 -top-1 h-2 w-2 rounded-full bg-lime-300" />
          </div>
           <div><div className="text-sm font-bold tracking-wide text-slate-100">CALSI</div><div className="mono text-[9px] tracking-[.22em] text-slate-500">SCIENTIFIC CALCULATOR</div></div>
        </div>
        <div className="hidden items-center gap-5 text-[11px] text-slate-500 sm:flex">
          <div className="flex items-center gap-1 rounded-lg border border-slate-700/70 bg-slate-900/40 p-1">
            {(['cyan', 'violet', 'lime', 'magenta'] as AccentTheme[]).map((theme) => <button data-testid={`button-accent-${theme}`} key={theme} onClick={() => setAccentTheme(theme)} aria-label={`Use ${theme} accent`} className={`accent-swatch ${theme} ${accentTheme === theme ? 'selected' : ''}`} />)}
          </div>
          <span className="flex items-center gap-2"><span className="h-1.5 w-1.5 rounded-full bg-lime-300" /> instrument online</span><span className="mono">v1.4.2</span>
        </div>
        <button data-testid="button-open-history" onClick={() => setShowHistory(true)} className="focus-ring flex items-center gap-2 rounded-lg border border-slate-700/80 bg-slate-900/40 px-3 py-2 text-xs font-semibold text-slate-300 transition hover:border-cyan-300/50 hover:text-cyan-200 sm:hidden"><History size={15} /> History</button>
      </header>

      <div className="mx-auto grid max-w-[1440px] gap-6 px-5 pb-12 sm:px-8 lg:grid-cols-[minmax(0,1fr)_370px] lg:px-12">
        <section>
          <div className="mb-6 max-w-2xl">
            <p className="eyebrow mb-3 flex items-center gap-2"><Zap size={13} /> instant feedback / exact notation</p>
            <h1 className="text-4xl font-semibold leading-[1.02] tracking-[-.05em] text-slate-100 sm:text-6xl">Think in <span className="text-cyan-200">patterns.</span><br /><span className="text-violet-300">Calculate</span> in light.</h1>
            <p className="mt-4 max-w-md text-sm leading-6 text-slate-400">A precise scientific instrument for the curious. No ceremony — just a clean signal between thought and answer.</p>
          </div>

          <div className="glass overflow-hidden rounded-2xl">
            <div className="flex flex-wrap items-center justify-between gap-3 border-b border-slate-700/60 px-4 py-3 sm:px-5">
             <div className="flex items-center gap-2"><Calculator size={16} className="text-cyan-200" /><span className="text-xs font-semibold tracking-wide text-slate-200">CALCULATOR</span><span className="mono rounded bg-slate-800 px-2 py-1 text-[9px] text-slate-500">LOCAL</span></div>
              <div className="flex items-center gap-1 rounded-lg border border-slate-700/70 bg-slate-950/40 p-1">
                {(['DEG', 'RAD', 'GRAD'] as AngleMode[]).map((mode) => <button data-testid={`button-angle-${mode.toLowerCase()}`} key={mode} onClick={() => setAngleMode(mode)} className={`focus-ring rounded-md px-2.5 py-1 text-[10px] font-bold tracking-wider transition ${angleMode === mode ? 'bg-cyan-300 text-slate-950 shadow-[0_0_14px_rgba(103,240,239,.3)]' : 'text-slate-500 hover:text-slate-200'}`}>{mode}</button>)}
              </div>
            </div>
            <div className="p-4 sm:p-6">
              <div className="mb-5 rounded-xl border border-slate-700/80 bg-[#0a0f1f] p-4 shadow-inner sm:p-5">
                <div className="flex min-h-5 items-center justify-between gap-3"><span className="mono text-[10px] tracking-[.16em] text-slate-600">EXPRESSION</span>{expression && <button data-testid="button-clear-expression" onClick={reset} className="focus-ring text-slate-600 transition hover:text-rose-300"><X size={15} /></button>}</div>
                <input data-testid="input-expression" aria-label="Scientific expression" value={expression} onChange={(e) => { setExpression(e.target.value); setError(''); }} onKeyDown={(e) => { if (e.key === 'Enter') calculate(); }} placeholder="Try  sin(45) + √(2)  or  12^3" className="mono mt-3 w-full bg-transparent text-right text-xl text-slate-200 outline-none placeholder:text-slate-700 sm:text-2xl" autoComplete="off" />
                <div className="mt-4 flex min-h-[58px] items-end justify-between gap-3 border-t border-slate-800 pt-3">
                  <div className="min-w-0">{error ? <p data-testid="status-calculation-error" className="flex items-start gap-2 text-xs leading-5 text-rose-300"><span className="mt-1 h-1.5 w-1.5 shrink-0 rounded-full bg-rose-300" />{error}</p> : <p className="mono text-[10px] text-slate-600">{result ? `${angleMode} · evaluated just now` : 'ready for a new observation'}</p>}</div>
                  <div className="flex items-end gap-2"><span className="text-xs text-slate-600">=</span><strong data-testid="text-calculation-result" className="mono max-w-[260px] overflow-hidden text-ellipsis text-3xl font-medium tracking-tight text-cyan-200 sm:text-4xl">{result || '0'}</strong></div>
                </div>
              </div>

               <div className="grid grid-cols-5 gap-2">
                 {[
                   ['2nd', 'deg', secondMode ? 'sin⁻¹' : 'sin', secondMode ? 'cos⁻¹' : 'cos', secondMode ? 'tan⁻¹' : 'tan'],
                   ['xʸ', 'lg', 'ln', '(', ')'],
                   ['√x', 'AC', '⌫', '%', '÷'],
                   ['x!', '7', '8', '9', '×'],
                   ['1/x', '4', '5', '6', '−'],
                   ['π', '1', '2', '3', '+'],
                   ['⇄', 'e', '0', '.', '='],
                 ].flat().map((label, index) => <Key key={`${label}-${index}`} label={label} onClick={() => label === '=' ? calculate() : handleKey(label)} kind={['÷', '×', '−', '+', 'xʸ', '%'].includes(label) ? 'operator' : ['sin', 'cos', 'tan', 'sin⁻¹', 'cos⁻¹', 'tan⁻¹', '(', ')', '√x', 'x!', '1/x'].includes(label) ? 'function' : ''} equals={label === '='} testId={`button-key-${label}`} />)}
               </div>
              <div className="mt-4 flex flex-wrap gap-2">
                <button data-testid="button-reset-calculator" onClick={reset} className="focus-ring flex items-center gap-2 rounded-lg px-2 py-2 text-[11px] font-semibold text-slate-500 transition hover:text-slate-200"><RotateCcw size={13} /> Clear deck <span className="mono text-[9px] text-slate-700">esc</span></button>
                {result && <button data-testid="button-copy-result" onClick={() => copy(result)} className="focus-ring ml-auto flex items-center gap-2 rounded-lg px-2 py-2 text-[11px] font-semibold text-cyan-300 transition hover:text-cyan-100">{copied ? <Check size={13} /> : <Copy size={13} />} {copied ? 'Copied' : 'Copy result'}</button>}
              </div>
            </div>
          </div>

          <div className="mt-5 grid gap-5 md:grid-cols-2">
           <div id="tools" className="glass rounded-2xl p-5">
              <div className="mb-4 flex items-center justify-between"><div><p className="eyebrow mb-1">quick tools</p><h2 className="text-lg font-semibold text-slate-100">Unit translator</h2></div><Ruler size={20} className="text-lime-300" /></div>
              <div className="mb-4 flex gap-1 overflow-auto rounded-lg border border-slate-700/70 bg-slate-950/30 p-1">{(Object.keys(converterData) as Category[]).map((item) => <button data-testid={`button-category-${item.toLowerCase()}`} key={item} onClick={() => changeCategory(item)} className={`focus-ring shrink-0 rounded-md px-2 py-1.5 text-[10px] font-semibold transition ${category === item ? 'bg-lime-300 text-slate-950' : 'text-slate-500 hover:text-slate-200'}`}>{item}</button>)}</div>
              <div className="grid grid-cols-[1fr_auto_1fr] items-end gap-2">
                <label className="min-w-0"><span className="mb-1 block text-[10px] text-slate-500">FROM</span><input data-testid="input-convert-value" value={convertValue} onChange={(e) => setConvertValue(e.target.value)} className="mono mb-2 w-full rounded-lg border border-slate-700 bg-slate-950/50 px-3 py-2 text-sm text-slate-200 outline-none focus:border-lime-300/60" /><select data-testid="select-convert-from" value={fromUnit} onChange={(e) => setFromUnit(e.target.value)} className="w-full rounded-lg border border-slate-700 bg-slate-900 px-2 py-2 text-[11px] text-slate-400 outline-none">{units.map((u) => <option key={u}>{u}</option>)}</select></label>
                <ArrowRightLeft size={15} className="mb-3 text-slate-600" />
                <label className="min-w-0"><span className="mb-1 block text-[10px] text-slate-500">TO</span><div data-testid="text-converted-value" className="mono mb-2 truncate rounded-lg border border-lime-300/20 bg-lime-300/[.06] px-3 py-2 text-sm text-lime-200">{converted}</div><select data-testid="select-convert-to" value={toUnit} onChange={(e) => setToUnit(e.target.value)} className="w-full rounded-lg border border-slate-700 bg-slate-900 px-2 py-2 text-[11px] text-slate-400 outline-none">{units.map((u) => <option key={u}>{u}</option>)}</select></label>
              </div>
            </div>
            <div className="glass rounded-2xl p-5">
              <div className="mb-4 flex items-center justify-between"><div><p className="eyebrow mb-1">extra tools</p><h2 className="text-lg font-semibold text-slate-100">Pocket instruments</h2></div><Sparkles size={19} className="text-fuchsia-300" /></div>
              <div className="mb-4 flex gap-1 rounded-lg border border-slate-700/70 bg-slate-950/30 p-1">
                 {(['Finance', 'Tip split', 'Percentage', 'Discount', 'Date', 'Numeral system', 'BMI', 'GST', 'Circle lab'] as ExtraTool[]).map((item) => <button data-testid={`button-extra-${item.toLowerCase().replaceAll(' ', '-')}`} key={item} onClick={() => setExtraTool(item)} className={`focus-ring shrink-0 rounded-md px-2 py-1.5 text-[10px] font-semibold transition ${extraTool === item ? 'bg-fuchsia-300 text-slate-950' : 'text-slate-500 hover:text-slate-200'}`}>{item}</button>)}
              </div>
               {extraTool === 'Circle lab' ? <div className="grid grid-cols-2 gap-2">
                 <ToolInput label="RADIUS" value={circleRadius} onChange={setCircleRadius} testId="input-circle-radius" />
                 <div data-testid="text-circle-area" className="rounded-lg border border-fuchsia-300/20 bg-fuchsia-300/[.06] p-3"><span className="block text-[9px] text-slate-500">AREA</span><strong className="mono mt-1 block text-lg text-fuchsia-200">{formatNumber(circleArea)}</strong></div>
                 <div data-testid="text-circle-circumference" className="col-span-2 rounded-lg border border-slate-700 bg-slate-950/40 p-3"><span className="block text-[9px] text-slate-500">CIRCUMFERENCE</span><strong className="mono mt-1 block text-lg text-slate-200">{formatNumber(circleCircumference)}</strong></div>
               </div> : extraTool === 'Date' ? <div className="grid grid-cols-2 gap-2">
                 <ToolInput label="DATE YYYY-MM-DD" value={dateValue} onChange={setDateValue} testId="input-date-value" />
                 <ToolInput label="DAYS TO ADD" value={dateOffset} onChange={setDateOffset} testId="input-date-offset" />
                 <div className="col-span-2 rounded-lg border border-fuchsia-300/20 bg-fuchsia-300/[.06] p-3"><span className="block text-[9px] text-slate-500">RESULT</span><strong className="mono mt-1 block text-lg text-fuchsia-200">{extraResult}</strong></div>
               </div> : <div className="grid grid-cols-3 gap-2">
                 <ToolInput label={extraTool === 'BMI' ? 'WEIGHT KG' : extraTool === 'Numeral system' ? 'DECIMAL' : extraTool === 'GST' || extraTool === 'Discount' ? 'AMOUNT' : extraTool === 'Tip split' ? 'BILL' : 'PRINCIPAL'} value={billAmount} onChange={setBillAmount} testId="input-bill-amount" />
                 <ToolInput label={extraTool === 'BMI' ? 'HEIGHT CM' : extraTool === 'Numeral system' ? 'BASE 2-36' : extraTool === 'Tip split' || extraTool === 'Percentage' ? 'PERCENT %' : 'RATE %'} value={tipPercent} onChange={setTipPercent} testId="input-tip-percent" />
                 {extraTool === 'Tip split' && <ToolInput label="PEOPLE" value={peopleCount} onChange={setPeopleCount} testId="input-people-count" />}
                 <div data-testid="text-extra-result" className={`${extraTool === 'Tip split' ? 'col-span-2' : 'col-span-3'} rounded-lg border border-fuchsia-300/20 bg-fuchsia-300/[.06] p-3`}><span className="block text-[9px] text-slate-500">RESULT</span><strong className="mono mt-1 block text-lg text-fuchsia-200">{extraResult}</strong></div>
               </div>}
              <div className="mt-4 flex items-center gap-2 text-[10px] text-fuchsia-300"><Keyboard size={14} /> all systems listening</div>
            </div>
          </div>
        </section>

        <aside className="hidden lg:block">
          <HistoryPanel history={history} onReplay={replay} onDelete={(id) => setHistory((items) => items.filter((item) => item.id !== id))} onClear={() => setHistory([])} onOpen={() => setShowHistory(true)} />
        </aside>
      </div>

      <footer className="mx-auto flex max-w-[1440px] items-center justify-between border-t border-slate-800/80 px-5 py-5 text-[10px] text-slate-600 sm:px-8 lg:px-12"><span className="mono">NEON SCIENTIFIC / FOR CURIOUS MINDS</span><span className="hidden sm:block">local-first · your calculations stay yours</span></footer>

      {showHistory && <div className="fixed inset-0 z-50 flex items-end justify-center bg-slate-950/75 p-0 backdrop-blur-sm sm:items-center sm:p-6"><div className="glass max-h-[90dvh] w-full max-w-2xl overflow-hidden rounded-t-2xl sm:rounded-2xl"><div className="flex items-center justify-between border-b border-slate-700/60 px-5 py-4"><div><p className="eyebrow mb-1">observatory log</p><h2 className="text-xl font-semibold text-slate-100">Full history</h2></div><button data-testid="button-close-history" onClick={() => setShowHistory(false)} className="focus-ring rounded-lg p-2 text-slate-500 hover:text-slate-100"><X size={18} /></button></div><div className="max-h-[65dvh] overflow-y-auto p-4"><HistoryPanel history={history} onReplay={replay} onDelete={(id) => setHistory((items) => items.filter((item) => item.id !== id))} onClear={() => setHistory([])} compact /></div></div></div>}
    </main>
  );
}

function Key({ label, icon, onClick, kind = '', equals = false, wide = false, testId }: { label?: string; icon?: ReactNode; onClick: () => void; kind?: string; equals?: boolean; wide?: boolean; testId: string }) {
  return <button data-testid={testId} onClick={onClick} className={`key focus-ring ${kind} ${equals ? 'equals' : ''} ${wide ? 'col-span-2' : ''} flex items-center justify-center text-lg font-medium ${equals ? 'col-span-1' : ''}`}>{icon || label}</button>;
}

function ToolInput({ label, value, onChange, testId }: { label: string; value: string; onChange: (value: string) => void; testId: string }) {
  return <label className="min-w-0"><span className="mb-1 block text-[9px] text-slate-500">{label}</span><input data-testid={testId} inputMode="decimal" value={value} onChange={(event) => onChange(event.target.value)} className="mono w-full rounded-lg border border-slate-700 bg-slate-950/50 px-3 py-2 text-sm text-slate-200 outline-none focus:border-fuchsia-300/60" /></label>;
}

function HistoryPanel({ history, onReplay, onDelete, onClear, onOpen, compact = false }: { history: HistoryItem[]; onReplay: (item: HistoryItem) => void; onDelete: (id: string) => void; onClear: () => void; onOpen?: () => void; compact?: boolean }) {
  return <div className={`glass rounded-2xl ${compact ? 'border-0 shadow-none' : 'sticky top-5'}`}>
    <div className="flex items-center justify-between border-b border-slate-700/60 px-5 py-4"><div className="flex items-center gap-2"><Clock3 size={16} className="text-violet-300" /><div><p className="eyebrow mb-0.5">memory bank</p><h2 className="text-base font-semibold text-slate-100">Recent calculations</h2></div></div><div className="flex items-center gap-1">{!compact && onOpen && <button data-testid="button-open-history-sidebar" onClick={onOpen} aria-label="Open full history" className="focus-ring rounded-md p-1.5 text-slate-600 hover:text-violet-200"><History size={14} /></button>}{history.length > 0 && <button data-testid={compact ? 'button-clear-history-modal' : 'button-clear-history'} onClick={onClear} className="focus-ring flex items-center gap-1.5 rounded-md px-2 py-1.5 text-[10px] font-semibold text-slate-500 hover:text-rose-300"><Trash2 size={12} /> Clear</button>}</div></div>
    {!history.length ? <div data-testid="status-history-empty" className="flex min-h-64 flex-col items-center justify-center px-5 text-center"><div className="mb-4 flex h-12 w-12 items-center justify-center rounded-full border border-dashed border-slate-700 text-slate-600"><Search size={18} /></div><p className="text-sm text-slate-400">No observations yet</p><p className="mt-1 max-w-[190px] text-xs leading-5 text-slate-600">Your evaluated expressions will land here, ready to replay.</p></div> : <div className="divide-y divide-slate-800/70">{history.slice(0, compact ? 100 : 5).map((item, index) => <div className="history-row group flex items-center gap-3 px-5 py-4" style={{ animationDelay: `${index * 45}ms` }} key={item.id} data-testid={`history-row-${item.id}`}><button data-testid={`button-replay-${item.id}`} onClick={() => onReplay(item)} className="focus-ring min-w-0 flex-1 text-left"><div className="mono truncate text-xs text-slate-500">{item.expression}</div><div data-testid={`text-history-result-${item.id}`} className="mono mt-1 text-base text-cyan-200">{item.result}</div></button><span className="mono hidden text-[9px] text-slate-700 sm:block">{item.mode}</span><button data-testid={`button-delete-history-${item.id}`} onClick={() => onDelete(item.id)} className="focus-ring rounded-md p-1.5 text-slate-700 opacity-0 transition group-hover:opacity-100 hover:text-rose-300"><Trash2 size={14} /></button></div>)}</div>}
    {!compact && history.length > 5 && <button data-testid="button-view-full-history" onClick={onOpen} className="focus-ring flex w-full items-center justify-center gap-2 border-t border-slate-700/60 px-5 py-3 text-[11px] font-semibold text-violet-300 transition hover:bg-violet-300/[.05]">View full log <MoreHorizontal size={14} /></button>}
  </div>;
}

export default App;

===== FILE: artifacts/neon-calculator/src/index.css =====
=======================================

@import url('https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Space+Grotesk:wght@400;500;600;700&display=swap');
@import 'tailwindcss';
@import 'tw-animate-css';
@plugin "@tailwindcss/typography";

@custom-variant dark (&:is(.dark *));

@theme inline {
  --color-background: hsl(var(--background));
  --color-foreground: hsl(var(--foreground));
  --color-border: hsl(var(--border));
  --color-input: hsl(var(--input));
  --color-ring: hsl(var(--ring));
  --color-card: hsl(var(--card));
  --color-card-foreground: hsl(var(--card-foreground));
  --color-card-border: hsl(var(--card-border));
  --color-popover: hsl(var(--popover));
  --color-popover-foreground: hsl(var(--popover-foreground));
  --color-popover-border: hsl(var(--popover-border));
  --color-primary: hsl(var(--primary));
  --color-primary-foreground: hsl(var(--primary-foreground));
  --color-secondary: hsl(var(--secondary));
  --color-secondary-foreground: hsl(var(--secondary-foreground));
  --color-muted: hsl(var(--muted));
  --color-muted-foreground: hsl(var(--muted-foreground));
  --color-accent: hsl(var(--accent));
  --color-accent-foreground: hsl(var(--accent-foreground));
  --color-destructive: hsl(var(--destructive));
  --color-destructive-foreground: hsl(var(--destructive-foreground));
  --radius-sm: calc(var(--radius) - 4px);
  --radius-md: calc(var(--radius) - 2px);
  --radius-lg: var(--radius);
  --radius-xl: calc(var(--radius) + 4px);
}

:root {
  --background: 0 0% 0%;
  --foreground: 0 0% 96%;
  --border: 0 0% 19%;
  --input: 0 0% 19%;
  --ring: 27 100% 50%;
  --card: 0 0% 10%;
  --card-foreground: 0 0% 96%;
  --card-border: 0 0% 19%;
  --popover: 0 0% 7%;
  --popover-foreground: 0 0% 96%;
  --popover-border: 0 0% 22%;
  --primary: 27 100% 50%;
  --primary-foreground: 0 0% 0%;
  --secondary: 27 100% 60%;
  --secondary-foreground: 0 0% 0%;
  --muted: 0 0% 14%;
  --muted-foreground: 0 0% 60%;
  --accent: 27 100% 60%;
  --accent-foreground: 0 0% 0%;
  --destructive: 348 96% 66%;
  --destructive-foreground: 228 31% 8%;
  --radius: 0.75rem;
  --app-font-sans: 'Space Grotesk', sans-serif;
  --app-font-mono: 'DM Mono', monospace;
  --app-font-serif: Georgia, serif;
}

html[data-accent='violet'] {
  --primary: 263 92% 76%;
  --secondary: 183 100% 67%;
  --accent: 77 100% 68%;
  --ring: 263 92% 76%;
}
html[data-accent='lime'] {
  --primary: 77 100% 68%;
  --secondary: 183 100% 67%;
  --accent: 313 100% 73%;
  --ring: 77 100% 68%;
}
html[data-accent='magenta'] {
  --primary: 313 100% 73%;
  --secondary: 263 92% 76%;
  --accent: 77 100% 68%;
  --ring: 313 100% 73%;
}

* { box-sizing: border-box; }
html { background: hsl(var(--background)); }
body {
  margin: 0;
  min-width: 320px;
  background: hsl(var(--background));
  color: hsl(var(--foreground));
  font-family: var(--app-font-sans);
  -webkit-font-smoothing: antialiased;
}
button, input, select { font: inherit; }
button { cursor: pointer; }
::selection { background: hsl(var(--primary) / .3); color: hsl(var(--foreground)); }

.instrument-shell {
  position: relative;
  isolation: isolate;
  min-height: 100dvh;
  overflow: hidden;
  background:
    radial-gradient(circle at 74% 12%, hsl(27 100% 50% / .08), transparent 28rem),
    radial-gradient(circle at 12% 80%, hsl(0 0% 35% / .08), transparent 32rem),
    hsl(var(--background));
}
.instrument-shell::before {
  content: "";
  position: fixed;
  z-index: -1;
  inset: 0;
  pointer-events: none;
  opacity: .24;
  background-image: linear-gradient(hsl(218 30% 50% / .07) 1px, transparent 1px), linear-gradient(90deg, hsl(218 30% 50% / .07) 1px, transparent 1px);
  background-size: 36px 36px;
  mask-image: linear-gradient(to bottom, black, transparent 78%);
}
.mono { font-family: var(--app-font-mono); }
.glass {
  background: linear-gradient(145deg, hsl(0 0% 12% / .96), hsl(0 0% 7% / .96));
  border: 1px solid hsl(var(--border));
  box-shadow: 0 24px 70px hsl(228 40% 3% / .22), inset 0 1px 0 hsl(255 80% 90% / .04);
}
.eyebrow { color: hsl(var(--primary)); font-size: 10px; font-weight: 700; letter-spacing: .18em; text-transform: uppercase; }
.focus-ring:focus-visible { outline: 2px solid hsl(var(--primary)); outline-offset: 3px; }
.accent-swatch { width: 14px; height: 14px; border-radius: 999px; border: 1px solid hsl(0 0% 100% / .18); opacity: .56; transition: transform .16s ease, opacity .16s ease, box-shadow .16s ease; }
.accent-swatch:hover, .accent-swatch.selected { opacity: 1; transform: scale(1.14); box-shadow: 0 0 12px currentColor; }
.accent-swatch.cyan { background: #67f0ef; color: #67f0ef; }
.accent-swatch.violet { background: #b99cff; color: #b99cff; }
.accent-swatch.lime { background: #c8ff60; color: #c8ff60; }
.accent-swatch.magenta { background: #ff73da; color: #ff73da; }
.key {
  min-height: 56px;
  border: 1px solid hsl(0 0% 22%);
  border-radius: 12px;
  color: hsl(210 35% 92%);
  background: linear-gradient(145deg, hsl(0 0% 17%), hsl(0 0% 12%));
  box-shadow: 0 4px 0 hsl(0 0% 4%), inset 0 1px 0 hsl(255 100% 100% / .06);
  transition: transform .16s ease, border-color .16s ease, color .16s ease, background .16s ease;
}
.key:hover { border-color: hsl(var(--primary) / .72); color: hsl(var(--primary)); background: linear-gradient(145deg, hsl(0 0% 22%), hsl(0 0% 15%)); }
.key:active { transform: translateY(3px); box-shadow: 0 1px 0 hsl(0 0% 4%), inset 0 1px 0 hsl(255 100% 100% / .04); }
.key.operator { color: hsl(var(--secondary)); border-color: hsl(27 80% 35%); }
.key.function { color: hsl(0 0% 68%); background: linear-gradient(145deg, hsl(0 0% 20%), hsl(0 0% 14%)); }
.key.equals { color: hsl(0 0% 0%); background: linear-gradient(135deg, hsl(27 100% 56%), hsl(22 100% 48%)); border-color: hsl(27 100% 64%); box-shadow: 0 5px 0 hsl(22 75% 29%), 0 0 25px hsl(27 100% 50% / .16); }
.key.equals:hover { color: hsl(0 0% 0%); filter: brightness(1.08); }
.history-row { animation: slide-in .32s ease both; }
@keyframes slide-in { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }
@keyframes pulse-dot { 0%,100% { opacity: .45; transform: scale(.86); } 50% { opacity: 1; transform: scale(1); } }
.pulse-dot { animation: pulse-dot 2.2s ease-in-out infinite; }
@media (prefers-reduced-motion: reduce) { *, *::before, *::after { animation-duration: .01ms !important; transition-duration: .01ms !important; } }
