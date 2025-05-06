/**
 * NFL Coaching Tree Visualization
 * 
 * An interactive visualization tool for exploring relationships 
 * between NFL head coaches and their coordinators.
 */

// Sample data for demonstration
const sampleData = `Season,head_coach,coordinator,role,team,wins,losses,ties
2021,Andy Reid,Eric Bieniemy,Offensive Coordinator,Kansas City Chiefs,12,5,0
2021,Andy Reid,Steve Spagnuolo,Defensive Coordinator,Kansas City Chiefs,12,5,0
2020,Andy Reid,Eric Bieniemy,Offensive Coordinator,Kansas City Chiefs,14,2,0
2020,Andy Reid,Steve Spagnuolo,Defensive Coordinator,Kansas City Chiefs,14,2,0
2021,Sean McVay,Kevin O'Connell,Offensive Coordinator,Los Angeles Rams,12,5,0
2021,Sean McVay,Raheem Morris,Defensive Coordinator,Los Angeles Rams,12,5,0
2020,Sean McVay,Kevin O'Connell,Offensive Coordinator,Los Angeles Rams,10,6,0
2020,Sean McVay,Brandon Staley,Defensive Coordinator,Los Angeles Rams,10,6,0
2022,Kevin O'Connell,Wes Phillips,Offensive Coordinator,Minnesota Vikings,13,4,0
2022,Kevin O'Connell,Ed Donatell,Defensive Coordinator,Minnesota Vikings,13,4,0
2022,Brandon Staley,Joe Lombardi,Offensive Coordinator,Los Angeles Chargers,10,7,0
2022,Brandon Staley,Renaldo Hill,Defensive Coordinator,Los Angeles Chargers,10,7,0
2019,Matt LaFleur,Nathaniel Hackett,Offensive Coordinator,Green Bay Packers,13,3,0
2019,Matt LaFleur,Mike Pettine,Defensive Coordinator,Green Bay Packers,13,3,0
2022,Nathaniel Hackett,Justin Outten,Offensive Coordinator,Denver Broncos,4,11,0
2022,Nathaniel Hackett,Ejiro Evero,Defensive Coordinator,Denver Broncos,4,11,0
2018,Sean McVay,Matt LaFleur,Offensive Coordinator,Los Angeles Rams,13,3,0
2018,Sean McVay,Wade Phillips,Defensive Coordinator,Los Angeles Rams,13,3,0`;

class CoachingTreeVisualization {
    /**
     * Initialize the coaching tree visualization
     */
    constructor() {
        // Core data structures
        this.coachingData = [];
        this.coaches = {};
        this.connections = [];
        this.activeInfoCard = null;
        
        // DOM elements
        this.treeElement = document.getElementById('coaching-tree');
        
        // Bind event handlers
        document.getElementById('load-data').addEventListener('click', () => this.loadData());
        document.getElementById('reset-view').addEventListener('click', () => this.resetView());
        document.getElementById('load-sample').addEventListener('click', () => this.loadSampleData());
        
        // Add keydown listener for Escape key to close info card
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') this.hideInfoCard();
        });
        
        // Set default tree dimensions
        this.treeWidth = 1200;
        this.treeHeight = 600;
        this.nodeRadius = 60;
        
        // Set up portfolio links
        this.setupPortfolioLinks();
    }
    
    /**
     * Set up portfolio and GitHub links
     */
    setupPortfolioLinks() {
        const portfolioLink = document.getElementById('portfolio-link');
        const githubLink = document.getElementById('https://github.com/Yush10');
        
        if (portfolioLink) {
            portfolioLink.href = "https://your-portfolio-url.com";
            portfolioLink.textContent = "Aayush Munshi";
        }
        
        if (githubLink) {
            githubLink.href = "https://github.com/Yush10/NFL_Coaching_Tree";
        }
    }
    
    /**
     * Load sample data into the visualization
     */
    loadSampleData() {
        document.getElementById('data-input').value = sampleData;
        this.loadData();
    }
    
    /**
     * Load and process data from input field
     */
    loadData() {
        const csvData = document.getElementById('data-input').value;
        if (!csvData) {
            this.showAlert('Please paste CSV data first');
            return;
        }
        
        // Parse CSV data
        this.coachingData = this.parseCSV(csvData);
        if (this.coachingData.length === 0) {
            this.showAlert('No valid data found');
            return;
        }
        
        // Process coaching data
        this.processCoachingData();
        
        // Calculate positions
        this.calculatePositions();
        
        // Render the visualization
        this.renderVisualization();
    }
    
    /**
     * Show alert message to the user
     * @param {string} message - The message to display
     */
    showAlert(message) {
        alert(message);
    }
    
    /**
     * Parse CSV text into structured data
     * @param {string} csvText - Raw CSV text
     * @returns {Array} - Array of objects representing data rows
     */
    parseCSV(csvText) {
        const lines = csvText.trim().split('\n');
        const headers = lines[0].split(',');
        
        // Check if we have the required headers
        const requiredHeaders = ['Season', 'head_coach', 'coordinator', 'role', 'team', 'wins', 'losses', 'ties'];
        const missingHeaders = requiredHeaders.filter(h => !headers.includes(h));
        
        if (missingHeaders.length > 0) {
            this.showAlert(`Missing required headers: ${missingHeaders.join(', ')}`);
            return [];
        }
        
        const data = [];
        for (let i = 1; i < lines.length; i++) {
            const values = lines[i].split(',');
            if (values.length === headers.length) {
                const row = {};
                headers.forEach((header, index) => {
                    row[header] = values[index];
                });
                data.push(row);
            }
        }
        
        return data;
    }
    
    /**
     * Process coaching data to build relationships
     */
    processCoachingData() {
        this.coaches = {};
        this.connections = [];
        
        // First pass: Collect all coaches and their roles
        this.coachingData.forEach(row => {
            const season = parseInt(row.Season);
            
            // Add head coach
            if (!this.coaches[row.head_coach]) {
                this.coaches[row.head_coach] = {
                    name: row.head_coach,
                    roles: [],
                    coordinatorsUnder: new Set(),
                    headCoachesOver: new Set(),
                    level: 0  // Level will be calculated later
                };
            }
            
            // Add head coach role if not already present for this season/team
            const existingHeadCoachRole = this.coaches[row.head_coach].roles.find(r => 
                r.season === season && r.team === row.team && r.role === 'Head Coach'
            );
            
            if (!existingHeadCoachRole) {
                this.coaches[row.head_coach].roles.push({
                    season: season,
                    team: row.team,
                    role: 'Head Coach',
                    record: `${row.wins}-${row.losses}-${row.ties}`
                });
            }
            
            // Add coordinator
            if (!this.coaches[row.coordinator]) {
                this.coaches[row.coordinator] = {
                    name: row.coordinator,
                    roles: [],
                    coordinatorsUnder: new Set(),
                    headCoachesOver: new Set(),
                    level: 0
                };
            }
            
            // Add coordinator role
            this.coaches[row.coordinator].roles.push({
                season: season,
                team: row.team,
                role: row.role,
                record: `${row.wins}-${row.losses}-${row.ties}`
            });
            
            // Create connections between head coach and coordinator
            this.coaches[row.head_coach].coordinatorsUnder.add(row.coordinator);
            this.coaches[row.coordinator].headCoachesOver.add(row.head_coach);
            
            // Store connection with specific team and season
            this.connections.push({
                head: row.head_coach,
                coordinator: row.coordinator,
                season: season,
                team: row.team
            });
        });
        
        // Calculate levels for positioning (how deep in the hierarchy)
        this.calculateLevels();
    }
    
    /**
     * Calculate hierarchical levels for coaches
     */
    calculateLevels() {
        // Find root coaches (those who were never coordinators or were head coaches first)
        const rootCoaches = Object.values(this.coaches).filter(coach => {
            // Coach was never a coordinator or was a head coach before being a coordinator
            const wasCoordinator = coach.roles.some(r => r.role !== 'Head Coach');
            const wasHeadCoach = coach.roles.some(r => r.role === 'Head Coach');
            
            if (!wasCoordinator) {
                return wasHeadCoach; // Only root if they were actually a head coach
            }
            
            // Find earliest seasons as head coach and coordinator
            const earliestHeadCoachSeason = wasHeadCoach ? 
                Math.min(...coach.roles
                    .filter(r => r.role === 'Head Coach')
                    .map(r => r.season)) : Infinity;
            
            const earliestCoordinatorSeason = wasCoordinator ?
                Math.min(...coach.roles
                    .filter(r => r.role !== 'Head Coach')
                    .map(r => r.season)) : Infinity;
            
            // Root coach if they were head coach first
            return wasHeadCoach && earliestHeadCoachSeason <= earliestCoordinatorSeason;
        });
        
        // Assign level 0 to root coaches
        rootCoaches.forEach(coach => {
            coach.level = 0;
        });
        
        // Calculate levels for all other coaches through BFS
        const queue = [...rootCoaches];
        const visited = new Set(rootCoaches.map(c => c.name));
        
        while (queue.length > 0) {
            const currentCoach = queue.shift();
            
            // Process all coordinators under this coach
            currentCoach.coordinatorsUnder.forEach(coordinatorName => {
                const coordinator = this.coaches[coordinatorName];
                
                // Set level to max of current level or head coach's level + 1
                coordinator.level = Math.max(coordinator.level, currentCoach.level + 1);
                
                // Add to queue if not visited
                if (!visited.has(coordinatorName)) {
                    visited.add(coordinatorName);
                    queue.push(coordinator);
                }
            });
        }
        
        // Handle any remaining coaches (those without clear hierarchical connections)
        Object.values(this.coaches).forEach(coach => {
            if (!visited.has(coach.name)) {
                const maxLevel = Object.values(this.coaches)
                    .filter(c => visited.has(c.name))
                    .reduce((max, c) => Math.max(max, c.level), 0);
                    
                coach.level = maxLevel + 1;
                visited.add(coach.name);
            }
        });
    }
    
    /**
     * Calculate positions for coach nodes in the visualization
     */
    calculatePositions() {
        // Group coaches by level
        const coachesByLevel = {};
        Object.values(this.coaches).forEach(coach => {
            if (!coachesByLevel[coach.level]) {
                coachesByLevel[coach.level] = [];
            }
            coachesByLevel[coach.level].push(coach);
        });
        
        // Count maximum number of coaches at any level
        const maxCoachesAtAnyLevel = Math.max(
            ...Object.values(coachesByLevel).map(coaches => coaches.length)
        );
        
        // Calculate total levels
        const totalLevels = Math.max(
            ...Object.values(this.coaches).map(c => c.level)
        ) + 1;
        
        // Adjust tree height based on number of levels
        this.treeHeight = Math.max(600, totalLevels * 200);
        
        // Adjust tree width based on maximum coaches at any level
        this.treeWidth = Math.max(1000, maxCoachesAtAnyLevel * 180);
        
        // Assign positions to coaches based on level
        Object.keys(coachesByLevel).forEach(level => {
            const coaches = coachesByLevel[level];
            const levelY = parseInt(level) * (this.treeHeight / totalLevels) + 100;
            
            // Sort coaches alphabetically within level for better organization
            coaches.sort((a, b) => a.name.localeCompare(b.name));
            
            coaches.forEach((coach, index) => {
                const spacing = this.treeWidth / (coaches.length + 1);
                const x = (index + 1) * spacing;
                
                coach.x = x;
                coach.y = levelY;
            });
        });
    }
    
    /**
     * Render the entire visualization
     */
    renderVisualization() {
        // Clear existing visualization
        this.treeElement.innerHTML = '';
        this.treeElement.style.width = `${this.treeWidth}px`;
        this.treeElement.style.height = `${this.treeHeight}px`;
        
        // Render connections first (so they appear behind nodes)
        this.renderConnections();
        
        // Render coach nodes
        this.renderCoachNodes();
    }
    
    /**
     * Render connection lines between coaches
     */
    renderConnections() {
        this.connections.forEach(connection => {
            const headCoach = this.coaches[connection.head];
            const coordinator = this.coaches[connection.coordinator];
            
            const connectionEl = document.createElement('div');
            connectionEl.className = 'connection';
            connectionEl.dataset.head = connection.head;
            connectionEl.dataset.coordinator = connection.coordinator;
            connectionEl.dataset.season = connection.season;
            connectionEl.dataset.team = connection.team;
            
            // Calculate position and rotation
            const dx = coordinator.x - headCoach.x;
            const dy = coordinator.y - headCoach.y;
            const distance = Math.sqrt(dx * dx + dy * dy);
            const angle = Math.atan2(dy, dx) * 180 / Math.PI;
            
            // Position connection
            connectionEl.style.left = `${headCoach.x}px`;
            connectionEl.style.top = `${headCoach.y}px`;
            connectionEl.style.width = `${distance}px`;
            connectionEl.style.transform = `rotate(${angle}deg)`;
            
            this.treeElement.appendChild(connectionEl);
        });
    }
    
    /**
     * Render coach nodes (circles)
     */
    renderCoachNodes() {
        Object.values(this.coaches).forEach(coach => {
            const nodeEl = document.createElement('div');
            nodeEl.className = 'coach-node';
            
            // Check if this coach was ever a head coach
            const wasHeadCoach = coach.roles.some(r => r.role === 'Head Coach');
            if (wasHeadCoach) {
                nodeEl.classList.add('head-coach');
            } else {
                nodeEl.classList.add('coordinator');
            }
            
            nodeEl.textContent = coach.name;
            nodeEl.style.left = `${coach.x - this.nodeRadius}px`;
            nodeEl.style.top = `${coach.y - this.nodeRadius}px`;
            nodeEl.dataset.coach = coach.name;
            
            // Add click event
            nodeEl.addEventListener('click', (e) => {
                this.showCoachInfo(coach, e.clientX, e.clientY);
            });
            
            this.treeElement.appendChild(nodeEl);
        });
    }
    
    /**
     * Show coach information in a popup card
     * @param {Object} coach - Coach data object
     * @param {number} clientX - Click X position
     * @param {number} clientY - Click Y position
     */
    showCoachInfo(coach, clientX, clientY) {
        // Remove any existing info card
        this.hideInfoCard();
        
        // Create new info card
        const infoCard = document.createElement('div');
        infoCard.className = 'info-card';
        
        // Add close button
        const closeBtn = document.createElement('span');
        closeBtn.className = 'close-btn';
        closeBtn.textContent = '×';
        closeBtn.addEventListener('click', (e) => {
            e.stopPropagation();
            this.hideInfoCard();
        });
        infoCard.appendChild(closeBtn);
        
        // Add coach name
        const nameHeading = document.createElement('h3');
        nameHeading.textContent = coach.name;
        infoCard.appendChild(nameHeading);
        
        // Sort roles by season (newest first)
        const sortedRoles = [...coach.roles].sort((a, b) => b.season - a.season);
        
        // Add career history
        sortedRoles.forEach(role => {
            const careerItem = document.createElement('div');
            careerItem.className = `career-item ${role.role === 'Head Coach' ? 'head-coach' : 'coordinator'}`;
            
            const teamYear = document.createElement('div');
            teamYear.className = 'team-year';
            teamYear.textContent = `${role.team} (${role.season})`;
            careerItem.appendChild(teamYear);
            
            const roleEl = document.createElement('div');
            roleEl.className = 'role';
            roleEl.textContent = role.role;
            careerItem.appendChild(roleEl);
            
            const recordEl = document.createElement('div');
            recordEl.className = 'record';
            recordEl.textContent = `Record: ${role.record}`;
            careerItem.appendChild(recordEl);
            
            // Add click event to highlight connected coaches
            careerItem.addEventListener('click', () => {
                this.highlightConnections(coach.name, role.team, role.season);
            });
            
            infoCard.appendChild(careerItem);
        });
        
        // Position the card
        const scrollX = window.scrollX;
        const scrollY = window.scrollY;
        const treeRect = this.treeElement.getBoundingClientRect();
        
        let left = clientX - treeRect.left + scrollX;
        let top = clientY - treeRect.top + scrollY;
        
        // Adjust position if it would go off screen
        if (left + 320 > treeRect.width) {
            left = left - 320;
        }
        
        infoCard.style.left = `${left}px`;
        infoCard.style.top = `${top}px`;
        
        // Add card to the tree
        this.treeElement.appendChild(infoCard);
        infoCard.style.display = 'block';
        
        this.activeInfoCard = infoCard;
    }
    
    /**
     * Hide the active info card
     */
    hideInfoCard() {
        if (this.activeInfoCard) {
            this.activeInfoCard.remove();
            this.activeInfoCard = null;
        }
    }
    
    /**
     * Highlight connections for a specific coach, team, and season
     * @param {string} coachName - Name of the coach
     * @param {string} team - Team name
     * @param {number} season - Season year
     */
    highlightConnections(coachName, team, season) {
        // Reset all highlights
        this.resetHighlights();
        
        // Find all connections for this coach, team, and season
        const relatedConnections = this.connections.filter(conn => 
            (conn.head === coachName || conn.coordinator === coachName) && 
            conn.team === team && 
            conn.season === parseInt(season)
        );
        
        // Highlight connections
        relatedConnections.forEach(conn => {
            const connectionEls = document.querySelectorAll(`.connection[data-head="${conn.head}"][data-coordinator="${conn.coordinator}"][data-season="${conn.season}"][data-team="${conn.team}"]`);
            connectionEls.forEach(el => {
                el.classList.add('highlighted');
            });
            
            // Highlight related coach nodes
            const headCoachEl = document.querySelector(`.coach-node[data-coach="${conn.head}"]`);
            const coordinatorEl = document.querySelector(`.coach-node[data-coach="${conn.coordinator}"]`);
            
            if (headCoachEl) headCoachEl.classList.add('highlighted');
            if (coordinatorEl) coordinatorEl.classList.add('highlighted');
        });
    }
    
    /**
     * Reset all highlights
     */
    resetHighlights() {
        document.querySelectorAll('.connection.highlighted').forEach(el => {
            el.classList.remove('highlighted');
        });
        
        document.querySelectorAll('.coach-node.highlighted').forEach(el => {
            el.classList.remove('highlighted');
        });
    }
    
    /**
     * Reset the entire visualization view
     */
    resetView() {
        this.resetHighlights();
        this.hideInfoCard();
    }
}

// Initialize visualization when the page loads
document.addEventListener('DOMContentLoaded', () => {
    const visualization = new CoachingTreeVisualization();
});
