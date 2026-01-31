# inventory_management
# Smart Supply Chain & Logistics Intelligence System

A comprehensive data-driven software solution for optimizing logistics, forecasting, traceability, and supply chain efficiency.

## 🚀 Project Overview

This hackathon project provides a complete supply chain management system with three distinct user interfaces:
- **Delivery Person & Product Owner Dashboard**: Manage products, vehicles, and track deliveries
- **Customer Tracking Portal**: Real-time delivery tracking with live map integration
- **AI/ML Integration**: Python-based live tracking system (to be integrated)

## 📋 Features

### For Delivery Personnel & Product Owners
- ✅ Secure login and signup system
- ✅ Dashboard with overview statistics
- ✅ Product management (Add, Edit, Delete)
- ✅ Vehicle fleet management
- ✅ Delivery tracking by product code
- ✅ Customer address management
- ✅ Real-time status updates

### For Customers
- ✅ Simple code-based authentication
- ✅ Delivery tracking with tracking code
- ✅ Live map integration (iframe to Python/AI-ML system)
- ✅ Delivery timeline visualization
- ✅ Real-time status updates

## 🎨 Design Features

- Modern, clean UI with gradient backgrounds
- Responsive design for all devices
- Sidebar navigation with smooth transitions
- Interactive tables with edit/delete functionality
- Modal forms for adding/editing data
- Status badges for visual status indicators
- Animated transitions and hover effects

## 🛠️ Technology Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Storage**: LocalStorage (simulating SQL database)
- **Design**: Custom CSS with gradients and animations
- **Integration**: Iframe for Python/AI-ML tracking system

## 📁 Project Structure

```
project/
│
├── index.html          # Main login/signup page
├── dashboard.html      # Dashboard for delivery person & product owner
├── tracking.html       # Customer tracking page with live map
└── README.md          # Project documentation
```

## 🚦 Getting Started

### Prerequisites
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Python/AI-ML tracking system running on `http://localhost:5000` (for live map feature)

### Installation

1. **Clone or download the project files**
   ```bash
   # Place all HTML files in a single directory
   ```

2. **Open the application**
   - Open `index.html` in your web browser
   - No server setup required for basic functionality

3. **Set up Python tracking system (Optional)**
   - Ensure your Python/AI-ML tracking system is running on port 5000
   - The map will automatically load in the iframe

## 👥 User Roles & Access

### 1. Delivery Person / Product Owner
**Sign Up:**
- Select user type (Delivery Person or Product Owner)
- Provide name, email, password, and phone number
- Creates account and logs in automatically

**Login:**
- Select user type
- Enter email and password
- Access full dashboard with all management features

**Test Credentials (After first signup):**
```
Email: demo@example.com
Password: demo123
Type: Product Owner or Delivery Person
```

### 2. Customer
**Login:**
- Select "Customer" as user type
- Enter delivery code (no email/password needed)

**Test Delivery Codes:**
```
DLV001 - Laptop Dell XPS (In Transit)
DLV002 - iPhone 15 Pro (Delivered)
DLV003 - Samsung TV 55" (In Transit)
```

## 📊 Dashboard Features

### Overview Section
- Total Products count
- Active Deliveries count
- Total Vehicles count
- Completed deliveries today

### Products Section
- View all products in a table
- Add new products with delivery details
- Edit existing product information
- Delete products
- Track product status (Pending, In Transit, Delivered)

### Vehicles Section
- View all vehicles in fleet
- Add new vehicles with driver details
- Edit vehicle information
- Delete vehicles
- Monitor vehicle status (Active, Inactive, Maintenance)

### Track Delivery Section
- Enter product/delivery code
- View live tracking map (integrates with Python system)
- Real-time location updates

## 🗄️ Data Storage

The application uses **LocalStorage** to simulate a SQL database with the following structure:

### Users Table
```javascript
{
  id: Number,
  userType: String,  // 'delivery' or 'owner'
  name: String,
  email: String,
  password: String,
  phone: String,
  createdAt: String
}
```

### Products Table
```javascript
{
  code: String,      // Unique product/delivery code
  name: String,
  customer: String,
  address: String,
  status: String     // 'Pending', 'In Transit', 'Delivered'
}
```

### Vehicles Table
```javascript
{
  id: String,
  type: String,      // 'Truck', 'Van', 'Bike', 'Car'
  plate: String,
  driver: String,
  status: String     // 'Active', 'Inactive', 'Maintenance'
}
```

### Delivery Codes Table
```javascript
{
  code: String,
  productName: String,
  status: String
}
```

## 🔗 Python Integration

The system is designed to integrate with your Python/AI-ML tracking system:

1. **Map Display**: The tracking pages use iframes pointing to `http://localhost:5000`
2. **Data Exchange**: You can extend the JavaScript to send delivery codes via API calls
3. **Real-time Updates**: The refresh button reloads the iframe to get latest tracking data

### Example Integration Code (for your Python system):
```python
# Flask example
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/')
def map_view():
    delivery_code = request.args.get('code', 'DLV001')
    # Your AI/ML tracking logic here
    return render_template('map.html', code=delivery_code)

if __name__ == '__main__':
    app.run(port=5000)
```

## 🎯 Usage Flow

### For Staff (Delivery Person/Product Owner):
1. Sign up or login through the main page
2. View dashboard with overview statistics
3. Navigate to Products section to manage deliveries
4. Navigate to Vehicles section to manage fleet
5. Use Track Delivery to monitor specific deliveries
6. Logout when finished

### For Customers:
1. Select "Customer" on login page
2. Enter delivery code (no email/password needed)
3. View delivery details and timeline
4. Track delivery on live map
5. Monitor real-time status updates

## 🔒 Security Notes

⚠️ **Important**: This is a prototype for hackathon demonstration purposes:
- Passwords are stored in plain text in LocalStorage
- No server-side validation
- No encryption
- LocalStorage can be cleared by users

**For production use, implement:**
- Server-side authentication
- Encrypted password storage (bcrypt, etc.)
- JWT tokens or session management
- HTTPS protocol
- Database (MySQL, PostgreSQL, MongoDB)
- Input validation and sanitization

## 🎨 Customization

### Changing Colors
Edit the CSS gradient colors in each HTML file:
```css
background: linear-gradient(135deg, #1e3c72 0%, #2a5298 50%, #7e8ba3 100%);
```

### Modifying Sidebar
Edit the `.sidebar-menu` section in `dashboard.html`:
```html
<div class="menu-item" onclick="showSection('newsection')">
    <span class="menu-icon">🆕</span>
    New Section
</div>
```

### Adding New Features
1. Create new section in the content area
2. Add corresponding menu item in sidebar
3. Implement JavaScript function to show/hide section
4. Add data structure in LocalStorage if needed

## 🐛 Troubleshooting

**Map not loading:**
- Ensure Python tracking system is running on port 5000
- Check browser console for CORS errors
- Verify iframe source URL in `dashboard.html` and `tracking.html`

**Login issues:**
- Clear browser cache and LocalStorage
- Check browser console for JavaScript errors
- Verify email and password are entered correctly

**Data not persisting:**
- Check if LocalStorage is enabled in browser
- Verify browser privacy settings allow LocalStorage
- Try using incognito/private mode

## 📱 Browser Compatibility

- ✅ Chrome (Recommended)
- ✅ Firefox
- ✅ Safari
- ✅ Edge
- ⚠️ Internet Explorer (Not supported)

## 🤝 Contributing

This is a hackathon project. Feel free to:
- Add new features
- Improve UI/UX
- Enhance security
- Add API integration
- Improve mobile responsiveness

## 📄 License

This project is created for educational and hackathon purposes.

## 👥 Team

Developed for Smart Supply Chain & Logistics Intelligence Hackathon

## 🎓 Future Enhancements

- [ ] Real backend database integration
- [ ] Advanced analytics dashboard
- [ ] Email/SMS notifications
- [ ] Multi-language support
- [ ] Mobile app version
- [ ] Advanced reporting features
- [ ] Route optimization
- [ ] Predictive analytics
- [ ] Blockchain for traceability
- [ ] IoT sensor integration

## 📞 Support

For issues or questions about the prototype, check:
1. Browser console for error messages
2. LocalStorage data in browser dev tools
3. Iframe integration with Python system
4. README troubleshooting section

---

**Built with ❤️ for Smart Supply Chain Innovation**
