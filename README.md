# Procedural SVG Cloud Generator

A lightweight, high-performance JavaScript library that generates procedurally created SVG clouds. Perfect for creating unique, randomized cloud graphics for web applications, games, and data visualizations without relying on static image assets.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Size](https://img.shields.io/badge/size-~15KB-brightgreen)

---

## 🌟 Features

- **Procedural Generation**: Creates unique, randomized cloud shapes every time
- **Lightweight**: Minimal dependencies, optimized for performance
- **Scalable Vector Graphics**: Pure SVG output that scales perfectly on any device
- **Customizable**: Extensive configuration options for shape, size, color, and animation
- **Mobile Optimized**: Responsive design with mobile-first approach
- **Animation Ready**: Built-in support for CSS animations and transitions
- **Multiple Cloud Types**: Generate different cloud styles (cumulus, stratus, cirrus)
- **No External Dependencies**: Vanilla JavaScript implementation
- **Browser Compatible**: Works on all modern browsers (Chrome, Firefox, Safari, Edge)
- **TypeScript Support**: Full TypeScript definitions included
- **Easy Integration**: Simple API for quick implementation

---

## 📦 Installation

### NPM
```bash
npm install procedural-cloud-svg-generator
```

### Yarn
```bash
yarn add procedural-cloud-svg-generator
```

### PNPM
```bash
pnpm add procedural-cloud-svg-generator
```

### CDN
```html
<script src="https://cdn.example.com/cloud-generator.min.js"></script>
```

### Manual Download
Clone the repository and include the library directly:
```html
<script src="./path/to/cloud-generator.js"></script>
```

---

## 🚀 Quick Start

### Basic Usage

```javascript
import { CloudGenerator } from 'procedural-cloud-svg-generator';

// Create a new cloud generator
const generator = new CloudGenerator();

// Generate a default cloud SVG
const cloudSVG = generator.generate();

// Insert into DOM
document.getElementById('container').innerHTML = cloudSVG;
```

### React Example

```jsx
import React, { useEffect, useRef } from 'react';
import { CloudGenerator } from 'procedural-cloud-svg-generator';

function CloudComponent() {
  const containerRef = useRef(null);

  useEffect(() => {
    const generator = new CloudGenerator();
    const cloudSVG = generator.generate();
    containerRef.current.innerHTML = cloudSVG;
  }, []);

  return <div ref={containerRef} />;
}

export default CloudComponent;
```

### Vue Example

```vue
<template>
  <div ref="cloudContainer"></div>
</template>

<script>
import { CloudGenerator } from 'procedural-cloud-svg-generator';

export default {
  mounted() {
    const generator = new CloudGenerator();
    const cloudSVG = generator.generate();
    this.$refs.cloudContainer.innerHTML = cloudSVG;
  }
</script>
```

### HTML Example

```html
<!DOCTYPE html>
<html>
<head>
  <script src="cloud-generator.js"></script>
</head>
<body>
  <div id="cloud-container"></div>
  
  <script>
    const generator = new CloudGenerator();
    const cloudSVG = generator.generate();
    document.getElementById('cloud-container').innerHTML = cloudSVG;
  </script>
</body>
</html>
```

---

## 📚 Usage Examples

### Example 1: Basic Cloud with Custom Size

```javascript
const generator = new CloudGenerator({
  width: 300,
  height: 150,
  fill: '#ffffff',
  opacity: 1
});

const cloud = generator.generate();
document.getElementById('clouds').innerHTML = cloud;
```

### Example 2: Colored Clouds

```javascript
const colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#FFA07A'];

colors.forEach(color => {
  const generator = new CloudGenerator({
    width: 200,
    height: 100,
    fill: color,
    opacity: 0.8
  });
  
  const container = document.createElement('div');
  container.innerHTML = generator.generate();
  document.getElementById('gallery').appendChild(container);
});
```

### Example 3: Animated Clouds

```javascript
const generator = new CloudGenerator({
  width: 400,
  height: 200,
  fill: '#ffffff',
  animation: {
    enabled: true,
    duration: 10,
    keyframes: 'float'
  },
  filter: {
    shadow: true,
    blur: 2
  }
});

const cloud = generator.generate();
document.getElementById('animated-clouds').innerHTML = cloud;

// Add CSS animation
const style = document.createElement('style');
style.textContent = `
  @keyframes float {
    0%, 100% { transform: translateX(0); }
    50% { transform: translateX(20px); }
  }
  
  svg {
    animation: float 10s ease-in-out infinite;
  }
`;
document.head.appendChild(style);
```

### Example 4: Multiple Clouds Background

```javascript
function createCloudBackground() {
  const container = document.getElementById('background');
  
  for (let i = 0; i < 5; i++) {
    const generator = new CloudGenerator({
      width: 300 + Math.random() * 200,
      height: 100 + Math.random() * 100,
      fill: '#ffffff',
      opacity: 0.6 + Math.random() * 0.3,
      seed: Math.random()
    });
    
    const cloudDiv = document.createElement('div');
    cloudDiv.style.position = 'absolute';
    cloudDiv.style.top = Math.random() * 300 + 'px';
    cloudDiv.style.left = Math.random() * 800 + 'px';
    cloudDiv.innerHTML = generator.generate();
    
    container.appendChild(cloudDiv);
  }
}

createCloudBackground();
```

### Example 5: Dark Mode Clouds

```javascript
const generator = new CloudGenerator({
  width: 250,
  height: 120,
  fill: '#2d3748',
  opacity: 0.9,
  stroke: '#1a202c',
  strokeWidth: 1.5,
  type: 'cumulus'
});

const cloud = generator.generate();
document.getElementById('dark-mode').innerHTML = cloud;
```

### Example 6: Gradient-filled Clouds

```javascript
const generator = new CloudGenerator({
  width: 300,
  height: 150,
  fill: 'url(#cloudGradient)',
  gradients: [
    {
      id: 'cloudGradient',
      type: 'linear',
      stops: [
        { offset: '0%', color: '#FF6B6B' },
        { offset: '100%', color: '#FFD93D' }
      ]
    }
  ]
});

const cloud = generator.generate();
document.getElementById('gradient-clouds').innerHTML = cloud;
```

---

## 🔌 API Reference

### CloudGenerator Class

#### Constructor

```javascript
new CloudGenerator(options)
```

**Parameters:**
- `options` (Object): Configuration object (optional)

#### Methods

##### `generate()`
Generates and returns an SVG cloud element as a string.

```javascript
const svgString = generator.generate();
```

**Returns:** `string` - SVG markup

**Example:**
```javascript
const cloud = new CloudGenerator();
const svgString = cloud.generate();
console.log(svgString);
```

##### `generateElement()`
Generates and returns an SVG cloud as a DOM element.

```javascript
const svgElement = generator.generateElement();
```

**Returns:** `SVGElement` - DOM SVG element

**Example:**
```javascript
const cloud = new CloudGenerator();
const element = cloud.generateElement();
document.body.appendChild(element);
```

##### `generateBatch(count)`
Generates multiple clouds at once.

```javascript
const clouds = generator.generateBatch(5);
```

**Parameters:**
- `count` (number): Number of clouds to generate

**Returns:** `Array<string>` - Array of SVG strings

**Example:**
```javascript
const cloud = new CloudGenerator();
const cloudArray = cloud.generateBatch(10);
cloudArray.forEach(svg => {
  const div = document.createElement('div');
  div.innerHTML = svg;
  document.getElementById('container').appendChild(div);
});
```

##### `setSeed(seed)`
Sets the random seed for reproducible cloud generation.

```javascript
generator.setSeed(12345);
```

**Parameters:**
- `seed` (number|string): Seed value

**Returns:** `CloudGenerator` - Self for chaining

**Example:**
```javascript
const cloud = new CloudGenerator();
cloud.setSeed('my-cloud').generate();
```

##### `updateOptions(newOptions)`
Updates generator options without recreating the instance.

```javascript
generator.updateOptions({ fill: '#ff0000', width: 400 });
```

**Parameters:**
- `newOptions` (Object): Partial options object

**Returns:** `CloudGenerator` - Self for chaining

**Example:**
```javascript
const cloud = new CloudGenerator();
cloud.updateOptions({ opacity: 0.5 }).generate();
```

##### `getOptions()`
Returns current configuration options.

```javascript
const currentOptions = generator.getOptions();
```

**Returns:** `Object` - Current options

---

## ⚙️ Configuration Options

### Basic Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `width` | number | 300 | SVG width in pixels |
| `height` | number | 150 | SVG height in pixels |
| `fill` | string | '#ffffff' | Cloud fill color (hex, rgb, or CSS color name) |
| `opacity` | number | 1 | Cloud opacity (0-1) |
| `stroke` | string | 'none' | Stroke color |
| `strokeWidth` | number | 0 | Stroke width in pixels |
| `viewBox` | string | Auto-calculated | Custom SVG viewBox |

### Shape Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `type` | string | 'cumulus' | Cloud type: 'cumulus', 'stratus', 'cirrus' |
| `density` | number | 0.6 | Cloud density (0-1, higher = more detailed) |
| `seed` | number\|string | random | Random seed for reproducibility |
| `bumpy` | number | 0.5 | Bumpiness level (0-1) |
| `scale` | number | 1 | Overall scale multiplier |
| `rotation` | number | 0 | Rotation in degrees |

### Animation Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `animation.enabled` | boolean | false | Enable animations |
| `animation.duration` | number | 5 | Animation duration in seconds |
| `animation.delay` | number | 0 | Animation delay in seconds |
| `animation.keyframes` | string | 'float' | Animation type: 'float', 'pulse', 'drift' |
| `animation.easing` | string | 'ease-in-out' | CSS easing function |
| `animation.loop` | boolean | true | Loop animation |

### Filter Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `filter.blur` | number | 0 | Blur amount (0-10) |
| `filter.shadow` | boolean | false | Enable drop shadow |
| `filter.shadowBlur` | number | 3 | Shadow blur radius |
| `filter.shadowColor` | string | 'rgba(0,0,0,0.3)' | Shadow color |
| `filter.shadowOffset` | object | {x: 0, y: 2} | Shadow offset |

### Gradient Options

```javascript
{
  gradients: [
    {
      id: 'cloudGradient',
      type: 'linear', // or 'radial'
      x1: '0%',
      y1: '0%',
      x2: '100%',
      y2: '100%',
      stops: [
        { offset: '0%', color: '#FF6B6B' },
        { offset: '100%', color: '#FFD93D' }
      ]
    }
  ]
}
```

### Complete Configuration Example

```javascript
const options = {
  // Size
  width: 400,
  height: 200,
  
  // Colors and appearance
  fill: '#ffffff',
  opacity: 0.9,
  stroke: '#e0e0e0',
  strokeWidth: 1,
  
  // Shape
  type: 'cumulus',
  density: 0.7,
  seed: 'my-cloud-001',
  bumpy: 0.6,
  scale: 1.2,
  rotation: 0,
  
  // Animation
  animation: {
    enabled: true,
    duration: 8,
    delay: 0,
    keyframes: 'float',
    easing: 'ease-in-out',
    loop: true
  },
  
  // Filters
  filter: {
    blur: 1,
    shadow: true,
    shadowBlur: 4,
    shadowColor: 'rgba(0, 0, 0, 0.2)',
    shadowOffset: { x: 0, y: 2 }
  },
  
  // Gradients
  gradients: []
};

const generator = new CloudGenerator(options);
```

---

## 📱 Mobile Integration Guides

### Responsive Cloud Generator

```javascript
class ResponsiveCloudGenerator {
  constructor(containerId, cloudCount = 3) {
    this.container = document.getElementById(containerId);
    this.cloudCount = cloudCount;
    this.resize = this.resize.bind(this);
  }

  init() {
    this.generateClouds();
    window.addEventListener('resize', this.resize);
  }

  getViewportDimensions() {
    return {
      width: window.innerWidth,
      height: window.innerHeight
    };
  }

  generateClouds() {
    const { width, height } = this.getViewportDimensions();
    this.container.innerHTML = '';

    for (let i = 0; i < this.cloudCount; i++) {
      const cloudWidth = Math.min(300, width * 0.8);
      const cloudHeight = Math.min(150, width * 0.4);

      const generator = new CloudGenerator({
        width: cloudWidth,
        height: cloudHeight,
        fill: '#ffffff',
        opacity: 0.8
      });

      const wrapper = document.createElement('div');
      wrapper.style.cssText = `
        position: absolute;
        top: ${Math.random() * height}px;
        left: ${Math.random() * width}px;
        z-index: ${i};
      `;
      wrapper.innerHTML = generator.generate();
      this.container.appendChild(wrapper);
    }
  }

  resize() {
    this.generateClouds();
  }

  destroy() {
    window.removeEventListener('resize', this.resize);
  }
}

// Usage
const responsive = new ResponsiveCloudGenerator('cloud-container', 5);
responsive.init();
```

### Mobile Touch Interaction

```javascript
class InteractiveCloudGenerator {
  constructor(containerId) {
    this.container = document.getElementById(containerId);
    this.clouds = [];
    this.setupTouchListeners();
  }

  setupTouchListeners() {
    this.container.addEventListener('touchstart', (e) => this.onTouchStart(e));
    this.container.addEventListener('touchmove', (e) => this.onTouchMove(e));
    this.container.addEventListener('click', (e) => this.generateCloudAtPoint(e));
  }

  onTouchStart(event) {
    const touch = event.touches[0];
    this.generateCloudAtPoint({ clientX: touch.clientX, clientY: touch.clientY });
  }

  onTouchMove(event) {
    // Optional: Generate clouds while dragging
  }

  generateCloudAtPoint(event) {
    const generator = new CloudGenerator({
      width: 150,
      height: 75,
      fill: '#ffffff',
      opacity: 0.7 + Math.random() * 0.3,
      animation: {
        enabled: true,
        duration: 5 + Math.random() * 5,
        keyframes: 'float'
      }
    });

    const wrapper = document.createElement('div');
    wrapper.style.cssText = `
      position: absolute;
      left: ${event.clientX}px;
      top: ${event.clientY}px;
      pointer-events: none;
    `;
    wrapper.innerHTML = generator.generate();
    this.container.appendChild(wrapper);

    // Remove after animation
    setTimeout(() => wrapper.remove(), 10000);
  }
}

// Usage
const interactive = new InteractiveCloudGenerator('touch-container');
```

### React Native Web Integration

```jsx
import React, { useState, useEffect } from 'react';
import { View, StyleSheet } from 'react-native-web';
import { CloudGenerator } from 'procedural-cloud-svg-generator';

const CloudBackgroundView = ({ children }) => {
  const [clouds, setClouds] = useState([]);

  useEffect(() => {
    const cloudElements = [];
    const generator = new CloudGenerator();

    for (let i = 0; i < 5; i++) {
      cloudElements.push({
        id: i,
        svg: generator.generateBatch(1)[0],
        top: Math.random() * 400,
        left: Math.random() * 800,
        opacity: 0.6 + Math.random() * 0.3
      });
    }

    setClouds(cloudElements);
  }, []);

  return (
    <View style={styles.container}>
      {clouds.map(cloud => (
        <View
          key={cloud.id}
          style={[
            styles.cloud,
            { top: cloud.top, left: cloud.left, opacity: cloud.opacity }
          ]}
          dangerouslySetInnerHTML={{ __html: cloud.svg }}
        />
      ))}
      {children}
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    position: 'relative',
    overflow: 'hidden'
  },
  cloud: {
    position: 'absolute'
  }
});

export default CloudBackgroundView;
```

### Performance Optimization for Mobile

```javascript
class OptimizedMobileCloudGenerator {
  constructor(containerId, options = {}) {
    this.container = document.getElementById(containerId);
    this.maxClouds = options.maxClouds || 3;
    this.quality = options.quality || 'medium'; // 'low', 'medium', 'high'
    this.useRAF = true;
    this.animationFrameId = null;
  }

  getQualitySettings() {
    const settings = {
      low: {
        width: 150,
        height: 75,
        density: 0.4,
        blur: 0,
        shadow: false
      },
      medium: {
        width: 250,
        height: 120,
        density: 0.6,
        blur: 1,
        shadow: false
      },
      high: {
        width: 350,
        height: 180,
        density: 0.8,
        blur: 2,
        shadow: true
      }
    };
    return settings[this.quality] || settings.medium;
  }

  generate() {
    const qualitySettings = this.getQualitySettings();
    const clouds = [];

    for (let i = 0; i < this.maxClouds; i++) {
      const generator = new CloudGenerator({
        ...qualitySettings,
        fill: '#ffffff',
        opacity: 0.8
      });

      clouds.push({
        id: i,
        element: generator.generateElement(),
        top: Math.random() * 300,
        left: Math.random() * 800
      });
    }

    this.renderClouds(clouds);
  }

  renderClouds(clouds) {
    if (this.useRAF) {
      this.animationFrameId = requestAnimationFrame(() => {
        this.container.innerHTML = '';
        clouds.forEach(cloud => {
          const wrapper = document.createElement('div');
          wrapper.style.cssText = `
            position: absolute;
            top: ${cloud.top}px;
            left: ${cloud.left}px;
            will-change: transform;
          `;
          wrapper.appendChild(cloud.element);
          this.container.appendChild(wrapper);
        });
      });
    }
  }

  destroy() {
    if (this.animationFrameId) {
      cancelAnimationFrame(this.animationFrameId);
    }
  }
}

// Usage
const mobile = new OptimizedMobileCloudGenerator('sky', { 
  quality: 'medium',
  maxClouds: 3 
});
mobile.generate();
```

### PWA Integration

```javascript
// service-worker.js
self.addEventListener('fetch', event => {
  if (event.request.url.includes('cloud-generator')) {
    event.respondWith(
      caches.match(event.request).then(response => {
        return response || fetch(event.request).then(response => {
          return caches.open('cloud-cache-v1').then(cache => {
            cache.put(event.request, response.clone());
            return response;
          });
        });
      })
    );
  }
});

// app.js
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('service-worker.js');
}

const generator = new CloudGenerator();
const cloud = generator.generate();
```

---

## 🎨 Cloud Types

### Cumulus
Puffy, cotton-like clouds - most common and recognizable.

```javascript
const generator = new CloudGenerator({ type: 'cumulus' });
```

### Stratus
Flat, layered clouds that form horizontal layers.

```javascript
const generator = new CloudGenerator({ type: 'stratus' });
```

### Cirrus
Thin, wispy, feathery clouds found at high altitude.

```javascript
const generator = new CloudGenerator({ type: 'cirrus' });
```

---

## 🔧 Advanced Techniques

### Seeding for Consistency

```javascript
// Same seed produces identical clouds
const gen1 = new CloudGenerator({ seed: 'cloud-1' });
const cloud1 = gen1.generate(); // Always the same

const gen2 = new CloudGenerator({ seed: 'cloud-1' });
const cloud2 = gen2.generate(); // Identical to cloud1
```

### Batch Generation

```javascript
const generator = new CloudGenerator();
const clouds = generator.generateBatch(100);

// Efficient rendering
const fragment = document.createDocumentFragment();
clouds.forEach(svg => {
  const div = document.createElement('div');
  div.innerHTML = svg;
  fragment.appendChild(div);
});
document.getElementById('container').appendChild(fragment);
```

### Custom Animation Keyframes

```javascript
const generator = new CloudGenerator({
  animation: { enabled: true }
});

const cloud = generator.generate();
document.getElementById('sky').innerHTML = cloud;

// Add custom CSS
const style = document.createElement('style');
style.textContent = `
  @keyframes customFloat {
    0% { transform: translateX(-50px) translateY(0); }
    50% { transform: translateX(50px) translateY(-20px); }
    100% { transform: translateX(-50px) translateY(0); }
  }
  
  svg { animation: customFloat 15s ease-in-out infinite; }
`;
document.head.appendChild(style);
```

---

## 📊 Performance Considerations

- **Memory**: Each cloud instance uses minimal memory (~5-10KB)
- **Rendering**: SVG rendering is hardware-accelerated on most browsers
- **Animation**: Use `transform` and `opacity` for best performance
- **Mobile**: Reduce density and blur for better mobile performance

### Performance Tips

1. Use `generateBatch()` instead of multiple `generate()` calls
2. Apply animations via CSS rather than JavaScript
3. Use `will-change` CSS property on animated elements
4. Limit cloud density on mobile devices
5. Cache generated SVGs if using the same configuration repeatedly

---

## 🧪 Testing

### Unit Testing Example

```javascript
import { CloudGenerator } from 'procedural-cloud-svg-generator';

describe('CloudGenerator', () => {
  it('should generate a valid SVG string', () => {
    const generator = new CloudGenerator();
    const svg = generator.generate();
    expect(svg).toContain('<svg');
    expect(svg).toContain('</svg>');
  });

  it('should respect custom dimensions', () => {
    const generator = new CloudGenerator({ width: 500, height: 250 });
    const svg = generator.generate();
    expect(svg).toContain('width="500"');
    expect(svg).toContain('height="250"');
  });

  it('should generate consistent clouds with same seed', () => {
    const gen1 = new CloudGenerator({ seed: 'test' });
    const gen2 = new CloudGenerator({ seed: 'test' });
    expect(gen1.generate()).toBe(gen2.generate());
  });
});
```

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📝 License

This project is licensed under the MIT License - see LICENSE file for details.

---

## 🙋 Support

- **Documentation**: Full docs available at [docs.example.com](https://docs.example.com)
- **Issues**: Report bugs at [GitHub Issues](https://github.com/s22binft1m01096-stack/procedural-cloud-svg-generator/issues)
- **Discussions**: Join our community at [GitHub Discussions](https://github.com/s22binft1m01096-stack/procedural-cloud-svg-generator/discussions)
- **Email**: support@example.com

---

## 🎉 Changelog

### v1.0.0 (2026-01-06)
- Initial release
- Core cloud generation engine
- Multiple cloud types (cumulus, stratus, cirrus)
- Comprehensive configuration options
- Animation support
- Mobile optimization
- TypeScript support

---

**Made with ❤️ by the Cloud Generator Team**
