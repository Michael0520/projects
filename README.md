# My Projects Monorepo

<a alt="Nx logo" href="https://nx.dev" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/nrwl/nx/master/images/nx-logo.png" width="45"></a>

A modern monorepo powered by **Nx**, **pnpm**, and **TypeScript** for building scalable applications and shared libraries.

## 🏗️ Project Structure

```
projects/
├── apps/                      # Applications
│   └── beautiful-code-snap/   # Code screenshot generator (React + Vite)
├── packages/                  # Shared libraries
├── nx.json                    # Nx workspace configuration
├── pnpm-workspace.yaml       # pnpm workspace configuration
└── .vercelignore             # Vercel deployment optimization
```

## 🚀 Applications

### Beautiful Code Snap
A modern code screenshot generator built with React, Vite, and Tailwind CSS.

- **Framework**: React 18 + Vite
- **Styling**: Tailwind CSS + shadcn/ui components
- **State Management**: Zustand
- **Code Highlighting**: highlight.js
- **Features**: Custom themes, fonts, backgrounds, export options
- **Status**: ✅ Deployed and Live

**Live Demo**: [https://www.michaello.me/projects/beautiful-code-snap/ →](https://www.michaello.me/projects/beautiful-code-snap/)

## 🛠️ Tech Stack

- **Build System**: Nx 21.3.11
- **Package Manager**: pnpm
- **Languages**: TypeScript
- **Deployment**: Vercel (Multiple Projects)
- **CI/CD**: GitHub Actions + Nx Cloud
- **Domain Strategy**: Single domain with path-based routing

## 📦 Quick Start

### Prerequisites
- Node.js 18+
- pnpm 8+

### Installation
```bash
# Clone the repository
git clone <repository-url>
cd projects

# Install dependencies
pnpm install

# Start development server
npx nx run @apps/beautiful-code-snap:dev
```

### Available Commands
```bash
# Development
npx nx run @apps/beautiful-code-snap:dev

# Build for production
npx nx build @apps/beautiful-code-snap --configuration=production

# Preview production build
pnpm --filter @apps/beautiful-code-snap preview

# Run tests
npx nx test @apps/beautiful-code-snap

# Lint code
npx nx lint @apps/beautiful-code-snap

# Type checking
npx nx typecheck @apps/beautiful-code-snap
```

### Generate New Library
```bash
npx nx g @nx/js:lib packages/my-lib --publishable --importPath=@packages/my-lib
```

## 🚀 Deployment

### Domain Structure
All projects are accessible through the main domain using the URL pattern:
`https://www.michaello.me/projects/{project-name}`

This is achieved through Vercel rewrites in the main domain's configuration that forward `/projects/*` requests to the respective project's Vercel deployment.

### Vercel Deployment Configuration

Each application in the monorepo is deployed as a separate Vercel project.

#### Beautiful Code Snap Configuration
In Vercel Dashboard → Project Settings:

```bash
# Build Command
npx nx build @apps/beautiful-code-snap --configuration=production

# Output Directory  
apps/beautiful-code-snap/dist

# Install Command
pnpm install

# Ignored Build Step (in Git settings)
npx nx-ignore @apps/beautiful-code-snap
```

### Adding New Applications
1. Create new app: `npx nx g @nx/react:app apps/my-new-app`
2. Create separate Vercel project
3. Configure with same pattern, replacing app name
4. Update main domain (michaello.me) vercel.json with rewrite rule:
   ```json
   {
     "source": "/projects/my-new-app/:match*",
     "destination": "https://my-new-app-michaello.vercel.app/:match*"
   }
   ```

## 🔧 Development Workflow

### Nx Commands
```bash
# View project graph
npx nx graph

# Run affected projects only
npx nx affected:build
npx nx affected:test

# Cache management
npx nx reset  # Clear cache
```

### TypeScript Sync
```bash
# Sync project references
npx nx sync

# Check sync in CI
npx nx sync:check
```

## 🔌 Extensions & Tools

### Nx Console
IDE extension for enhanced developer experience:
- [VSCode Extension](https://marketplace.visualstudio.com/items?itemName=nrwl.angular-console)
- [IntelliJ Plugin](https://plugins.jetbrains.com/plugin/21060-nx-console)

### Nx Cloud
Connected workspace for advanced features:
- Remote caching
- Distributed task execution  
- CI analytics
- [Setup Nx Cloud →](https://cloud.nx.app/connect/OAGliXY8R2)

## 📚 Resources

### Documentation
- [Nx Documentation](https://nx.dev)
- [Nx Monorepo Guide](https://nx.dev/concepts/more-concepts/applications-and-libraries)
- [Vercel Deployment](https://vercel.com/docs/monorepos/nx)
- [pnpm Workspaces](https://pnpm.io/workspaces)

### Community
- [Nx Discord](https://go.nx.dev/community)
- [Nx on X/Twitter](https://twitter.com/nxdevtools)
- [Nx YouTube](https://www.youtube.com/@nxdevtools)

---

## 📄 License

MIT © [Michael0520](https://github.com/Michael0520)
