# React Artifact Development Guide for Claude's Renderer

## Critical Constraints - Will Break Artifacts ⚠️

These constraints are specific to Claude's artifact renderer and will cause complete failure if violated.

### 1. Blocked HTML Elements

#### ❌ Form Element - BLOCKED
```jsx
// NEVER use <form> elements - they are blocked and will cause artifact failure
<form onSubmit={handleSubmit}>
  <input type="text" />
  <button type="submit">Submit</button>
</form>
```

#### ✅ Use Event Handlers Instead
```jsx
// ALWAYS use <div> with onClick handlers instead of form submission
// Use React event handlers (onClick, onChange) for all user interactions
<div>
  <input 
    type="text" 
    value={value}
    onChange={(e) => setValue(e.target.value)}
    onKeyDown={(e) => e.key === 'Enter' && handleSubmit()}
  />
  <button onClick={handleSubmit}>Submit</button>
</div>
```

### 2. Import Alias Syntax - Not Supported

#### ❌ Import Aliases Cause "Unsupported Libraries" Error
```jsx
// The 'as' keyword in imports breaks the artifact renderer
import { Home as HomeIcon } from 'lucide-react';
import { Settings as SettingsIcon, User as UserIcon } from 'lucide-react';

// The renderer incorrectly parses "Home as HomeIcon" as a library name
const Navigation = () => (
  <nav>
    <HomeIcon /> {/* This will fail before rendering */}
  </nav>
);
```

#### ✅ Use Direct Imports
```jsx
// Use direct imports without aliases
import { Home, Settings, User } from 'lucide-react';

// Handle naming conflicts with wrapper components
const HomeIcon = () => <Home className="w-5 h-5" />;
const SettingsIcon = () => <Settings className="w-5 h-5" />;

// Or use the icons directly with descriptive variable names
const NavigationHome = Home;
const NavigationSettings = Settings;

// Multiple import lines from same library work fine
import { Home } from 'lucide-react';
import { Settings } from 'lucide-react';
import { User } from 'lucide-react';
```

### 3. Import Statement Formatting - Critical Rules

#### ❌ Trailing Commas in Multi-line Imports - PRIMARY FAILURE CAUSE
```jsx
// NEVER use trailing commas in multi-line imports
import {
  GitBranch,
  Lock,
  Package,  // <- This trailing comma WILL cause failure
} from 'lucide-react';
```

#### ❌ Empty Lines Within Imports
```jsx
// NEVER leave empty lines inside import statements
import {
  GitBranch,
  
  Package  // <- Empty line above breaks the parser
} from 'lucide-react';
```

#### ❌ Comments Within Import Statements
```jsx
// NEVER put comments inside import statements
import {
  GitBranch, // version control <- This comment is parsed as a library name
  Lock,      // security        <- Will cause "unsupported libraries" error
} from 'lucide-react';
```

#### ✅ Clean Multi-line Import Format
```jsx
// Use clean formatting without trailing commas, empty lines, or comments
import {
  GitBranch,
  Lock,
  Package,
  Shield,
  Server
} from 'lucide-react';

// Put comments about imports outside the statement
// GitBranch - version control, Lock - security features
```

### 4. Browser Storage - Not Available

#### ❌ All Storage APIs Are Forbidden
```jsx
// These will cause complete artifact failure
localStorage.setItem('data', JSON.stringify(data));
sessionStorage.setItem('temp', value);
document.cookie = 'user=John';
const db = indexedDB.open('MyDB');

// Even reading will fail
const saved = localStorage.getItem('data') || '{}';
```

#### ✅ Use React State Only
```jsx
// Component state
const [data, setData] = useState(null);

// Complex state with useReducer
const [state, dispatch] = useReducer(reducer, initialState);

// In-memory cache
const cache = useRef({});
cache.current[key] = value;

// Context for cross-component state
const StateContext = React.createContext();
```

## Renderer-Specific Constraints

### 5. Tailwind CSS - Only Pre-Compiled Classes

#### ❌ Dynamic Classes Will Break
```jsx
// Template literals - NEVER USE
className={`bg-${color}-500/20 text-${color}-400`}
className={`w-[${width}px] h-[${height}px]`}

// Dynamic construction with variables
const prefix = 'bg-';
className={`${prefix}${color}-500`}

// Arbitrary values
className="w-[537px] h-[293px]"
```

#### ✅ Use Complete Class Names
```jsx
// Complete class names in conditionals
className={
  color === 'blue' ? 'bg-blue-500/20 text-blue-400' :
  color === 'red' ? 'bg-red-500/20 text-red-400' :
  'bg-gray-500/20 text-gray-400'
}

// Object mapping with full classes
const colorClasses = {
  blue: 'bg-blue-500/20 text-blue-400 border-blue-500/50',
  red: 'bg-red-500/20 text-red-400 border-red-500/50',
  green: 'bg-green-500/20 text-green-400 border-green-500/50'
};
return colorClasses[color] || colorClasses.blue;

// Standard Tailwind utilities only
className="w-64 h-32" // Not w-[537px]
```

### 6. Available Libraries Only

#### ❌ Unavailable Libraries
```jsx
// These imports will fail
import moment from 'moment';
import axios from 'axios';
import { OrbitControls } from 'three/examples';
import customLib from 'any-npm-package';

// Three.js newer features (r128 doesn't have these)
new THREE.CapsuleGeometry(); // Added in r142
new THREE.SkeletonUtils();   // Not in r128
```

#### ✅ Available Libraries
```jsx
// React (must import hooks)
import { useState, useEffect, useCallback, useMemo } from 'react';

// Available libraries for React artifacts
import { Icon1, Icon2 } from 'lucide-react';
import { LineChart, BarChart } from 'recharts';
import * as math from 'mathjs';
import _ from 'lodash';
import * as d3 from 'd3';
import * as Plotly from 'plotly';
import * as THREE from 'three'; // r128 only - older version!
import Papa from 'papaparse';
import * as XLSX from 'xlsx';
import { Alert } from '@/components/ui/alert';
import * as Chart from 'chart.js';
import * as Tone from 'tone';

// HTML artifacts - CDN only
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
```

#### ❌ CSS-in-JS Not Supported
```jsx
// These will NOT work
import styled from 'styled-components';
import { css } from '@emotion/react';
// No CSS Modules
// No runtime CSS generation
```

### 7. Console Methods Limitations

#### ❌ Limited Console API
```jsx
// These console methods don't work
console.assert()  // Will not output
console.table()   // Will not output
console.dir()     // Will not output
```

#### ✅ Working Console Methods
```jsx
// Only these work reliably
console.log('Debug message');
console.warn('Warning message');
console.error('Error message');
```

### 8. Web APIs Limitations

#### ❌ Blocked Browser APIs
```jsx
// Storage (already covered)
localStorage, sessionStorage, indexedDB

// Workers
new Worker(), new ServiceWorker()

// Real-time Communication
new WebSocket(), RTCPeerConnection

// Device APIs
navigator.geolocation
navigator.clipboard
Notification.requestPermission()

// Media
navigator.mediaDevices.getUserMedia()
```

### 9. File System Access Pattern

#### ❌ Wrong Approach
```jsx
// No sync methods
const data = fs.readFileSync('file.csv');

// No Node.js APIs
const fs = require('fs');

// No error handling
const content = await window.fs.readFile('data.csv');
```

#### ✅ Correct Pattern
```jsx
// Always handle errors
const safeReadFile = async (filename) => {
  try {
    const data = await window.fs.readFile(filename, { encoding: 'utf8' });
    return { success: true, data };
  } catch (error) {
    console.error(`Failed to read ${filename}:`, error);
    return { success: false, error: error.message };
  }
};

// For CSV files specifically
const parseCSV = async (filename) => {
  const { success, data } = await safeReadFile(filename);
  if (!success) return null;
  
  return Papa.parse(data, {
    header: true,
    dynamicTyping: true,
    skipEmptyLines: true,
    delimitersToGuess: [',', '\t', '|', ';']
  });
};
```

### 10. Component Structure Requirements

#### ❌ Won't Work Properly
```jsx
// No default export
export const MyComponent = () => <div>Hello</div>;

// Required props without defaults
const Button = ({ onClick, text, variant }) => (
  <button onClick={onClick} className={variant}>{text}</button>
);

// Module syntax in HTML artifacts
<script type="module">
  import { something } from './module.js';
</script>

// Async components
const MyComponent = async () => { // Won't work
  const data = await fetchData();
  return <div>{data}</div>;
};
```

#### ✅ Required Structure
```jsx
// Must use default export
const MyComponent = ({ 
  // All props must have defaults
  title = 'Default Title',
  onClose = () => {},
  variant = 'primary'
}) => {
  return <div>{title}</div>;
};

export default MyComponent;

// Async in useEffect or handlers only
const MyComponent = () => {
  const [data, setData] = useState(null);
  
  useEffect(() => {
    const loadData = async () => {
      const result = await window.fs.readFile('data.csv');
      setData(result);
    };
    loadData();
  }, []);
  
  return <div>{data || 'Loading...'}</div>;
};

// HTML artifacts - inline everything
<script>
  // All code must be inline
  const data = [1, 2, 3];
</script>
```

## TypeScript Full Support ✅

### Fully Supported TypeScript Features
Unlike many sandboxed environments, React artifacts have **complete TypeScript support**:

- ✅ All type annotations and interfaces
- ✅ Generic components and functions
- ✅ React.FC and React type definitions  
- ✅ Complex types (unions, intersections, mapped types)
- ✅ Type imports and exports
- ✅ Const assertions
- ✅ Enums and type aliases

```tsx
// All of this works perfectly in React artifacts
interface Props<T> {
  items: T[];
  renderItem: (item: T) => React.ReactNode;
}

const List: React.FC<Props<string>> = ({ items, renderItem }) => {
  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>{renderItem(item)}</li>
      ))}
    </ul>
  );
};

// Complex types work fine
type Status = 'idle' | 'loading' | 'success' | 'error';
const [status, setStatus] = useState<Status>('idle');

// As const assertions
const COLORS = {
  primary: '#007bff',
  secondary: '#6c757d'
} as const;
```

**Note**: While TypeScript is fully supported for development, all other constraints still apply (no localStorage, no forms, etc.).

## Performance Considerations

### Artifact Size and Complexity
- Keep artifacts under ~2000 lines for best performance
- Batch state updates when possible
- For lists with 1000+ items, consider virtualization
- Use CSS transitions over JavaScript animations when possible

### Import Quantity
- ✅ No practical limit on number of imports (tested up to 30+)
- ✅ Multiple import statements from same library allowed
- ✅ Can split large import lists across multiple lines (without trailing commas!)

## Code Organization Patterns for Extensibility

### Type-Safe Constants Pattern

```jsx
/* ---------------------------------------------------------------------
 *  Types
 * -------------------------------------------------------------------*/
type Tool = {
  name: string;
  status: 'active' | 'inactive' | 'pending';
  icon: React.ElementType;
  category: string;
};

/* ---------------------------------------------------------------------
 *  Constants - Easy to extend
 * -------------------------------------------------------------------*/
const DEVOPS_TOOLS = [
  { name: 'GitLab', status: 'active', icon: GitBranch, category: 'vcs' },
  { name: 'Jenkins', status: 'active', icon: Server, category: 'ci' },
  { name: 'ArgoCD', status: 'pending', icon: RefreshCw, category: 'cd' }
  // Adding new tool = just add new object (no trailing comma!)
] as const;

// Derived data from constants
const ACTIVE_TOOLS = DEVOPS_TOOLS.filter(t => t.status === 'active');
const TOOL_CATEGORIES = [...new Set(DEVOPS_TOOLS.map(t => t.category))];
```

### Generic State Management

```jsx
// Generic expandable state - no need for multiple useState
const [expanded, setExpanded] = useState<Record<string, boolean>>({});
const toggleExpanded = (id: string) => 
  setExpanded(prev => ({ ...prev, [id]: !prev[id] }));

// Generic selection state
const [selected, setSelected] = useState<Set<string>>(new Set());
const toggleSelected = (id: string) => 
  setSelected(prev => {
    const next = new Set(prev);
    next.has(id) ? next.delete(id) : next.add(id);
    return next;
  });

// Centralized form data (no <form> elements!)
const [formData, setFormData] = useState<Record<string, any>>({});
const updateField = (field: string, value: any) =>
  setFormData(prev => ({ ...prev, [field]: value }));

// Handle submission without form element
const handleSubmit = () => {
  if (validateFormData(formData)) {
    processData(formData);
  }
};
```

### Error Boundary Pattern

```jsx
// Add error boundaries for robustness
class ErrorBoundary extends React.Component {
  state = { hasError: false, error: null };
  
  static getDerivedStateFromError(error) {
    return { hasError: true, error };
  }
  
  componentDidCatch(error, errorInfo) {
    console.error('Error caught:', error, errorInfo);
  }
  
  render() {
    if (this.state.hasError) {
      return (
        <div className="p-4 bg-red-50 border border-red-200 rounded">
          <h2 className="text-red-800">Something went wrong</h2>
          <pre className="text-sm">{this.state.error?.toString()}</pre>
        </div>
      );
    }
    return this.props.children;
  }
}

// Usage
<ErrorBoundary>
  <YourComponent />
</ErrorBoundary>
```

### Claude API Integration Pattern

```jsx
// Maintain conversation context
const useClaudeChat = () => {
  const [messages, setMessages] = useState<Array<{role: string, content: string}>>([]);
  const [loading, setLoading] = useState(false);
  
  const sendMessage = async (content: string) => {
    const userMessage = { role: 'user', content };
    const updatedMessages = [...messages, userMessage];
    
    setLoading(true);
    try {
      const response = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-20250514",
          max_tokens: 1000,
          messages: updatedMessages // Full history required
        })
      });
      
      const data = await response.json();
      const assistantMessage = {
        role: 'assistant',
        content: data.content[0].text
      };
      
      setMessages([...updatedMessages, assistantMessage]);
      return assistantMessage.content;
    } catch (error) {
      console.error('Claude API error:', error);
      return null;
    } finally {
      setLoading(false);
    }
  };
  
  return { messages, sendMessage, loading };
};

// API Rate Limiting Considerations
// - No explicit rate limits in artifact environment
// - Implement debouncing for user input
// - Add reasonable delays between rapid requests
```

### Special String Handling

```jsx
// Be careful with backticks in template literals
const codeExample = `This is a \`backtick\` example`; // Escape backticks

// For displaying code snippets
const codeSnippet = String.raw`
  const example = \`template literal\`;
`;
```

## Lucide React Icon Guidelines

### Icon Props
```jsx
// All Lucide icons accept these props
<Home size={24} />           // or width/height
<Settings className="w-6 h-6" />
<User strokeWidth={1.5} />
<Search color="#007bff" />
```

## Quick Reference Checklist

### ✅ Must Do
- [ ] Use complete Tailwind class names (no templates)
- [ ] Import React hooks explicitly
- [ ] Handle all errors in file/API operations
- [ ] Provide defaults for all component props
- [ ] Use default export for React components
- [ ] Keep all state in React (no localStorage)
- [ ] Replace forms with div + onClick handlers
- [ ] Use direct imports without `as` aliases
- [ ] Remove trailing commas from multi-line imports
- [ ] Keep imports clean (no comments or empty lines)
- [ ] Escape backticks in template literals
- [ ] Use ErrorBoundary for robust error handling

### ❌ Must Avoid  
- [ ] Dynamic class construction (`bg-${color}-500`)
- [ ] Browser storage (localStorage, cookies)
- [ ] HTML form elements (`<form>`)
- [ ] External NPM packages not in approved list
- [ ] Required props without defaults
- [ ] Multiple artifacts in one response
- [ ] Node.js APIs or sync file operations
- [ ] Import aliases with `as` keyword (`import { X as Y }`)
- [ ] Trailing commas in multi-line imports
- [ ] Empty lines within import statements
- [ ] Comments inside import statements
- [ ] CSS-in-JS libraries
- [ ] console.table(), console.assert(), console.dir()
- [ ] Async component functions

### 🎯 For Easy Modification
- [ ] Define data as typed constants with `as const`
- [ ] Use consistent object shapes
- [ ] Create builder functions for complex data
- [ ] Use generic state for UI patterns
- [ ] Follow naming conventions (handle*/on* for events)
- [ ] Extract domain-specific components
- [ ] Include error boundaries for robustness
- [ ] Use TypeScript for better IDE support
- [ ] Keep imports organized and clean
