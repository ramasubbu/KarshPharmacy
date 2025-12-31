# Pharmacy Inventory Management System

## Overview
This is a comprehensive Pharmacy Inventory Management System built with .NET MAUI Blazor, featuring:

- **Cross-platform support**: Mobile, Desktop, and Web
- **Offline/Online sync**: Works offline with SQLite, syncs to MySQL
- **Role-based access control**: Admin, Manager, and SalesPerson roles
- **Comprehensive reporting**: Business intelligence and analytics
- **Tally ERP integration**: Sync data with Tally accounting software
- **Modern UI**: MudBlazor components with Material Design

## Role-Based Access Control

### 🔐 User Roles

#### 1. **Admin** (Full Access)
- **Dashboard**: Complete overview with all metrics
- **Sales & Billing**: All sales operations
- **Inventory Management**: Products, categories, manufacturers, batches, stock alerts
- **Purchase Management**: Orders, purchases, suppliers
- **Customer & Doctor Management**: Complete access
- **Reports & Analytics**: All reports and business intelligence
- **Settings**: User management, company settings, backup, permissions
- **Tally Sync**: Integration management

#### 2. **Manager** (Inventory + Sales)
- **Dashboard**: Sales and inventory metrics
- **Sales & Billing**: All sales operations including returns
- **Inventory Management**: Products, categories, manufacturers, batches, stock alerts
- **Purchase Management**: Orders, purchases, suppliers
- **Customer & Doctor Management**: Complete access
- **Tally Sync**: Basic sync operations
- **❌ No Access**: Reports, Settings, User Management

#### 3. **SalesPerson** (Sales Only)
- **Dashboard**: Basic sales metrics
- **Sales & Billing**: New sales and sales history only
- **❌ No Access**: Inventory management, purchases, reports, settings

## Demo Accounts

### Quick Login Options Available:
1. **Admin Demo**: Username: `admin` / Password: `admin123`
2. **Manager Demo**: Username: `manager` / Password: `manager123`
3. **SalesPerson Demo**: Username: `sales` / Password: `sales123`

## Key Features by Role

### Admin Features
- **Complete Dashboard**: Revenue, profit, inventory status, alerts
- **Comprehensive Reports**:
  - Sales reports with charts and analytics
  - Product performance analysis
  - Inventory status and valuation
  - Customer purchase patterns
  - Supplier performance
  - Expiry tracking and alerts
  - Profit & Loss statements
  - Custom date range filtering
- **User Management**: Create, edit, deactivate users
- **System Settings**: Company profile, backup/restore
- **Advanced Analytics**: Trends, forecasting, KPIs

### Manager Features
- **Product Management**: Add, edit, categorize products
- **Inventory Control**: Stock management, batch tracking
- **Purchase Operations**: Order management, supplier relations
- **Sales Processing**: Complete sales operations
- **Stock Alerts**: Low stock and expiry notifications

### SalesPerson Features
- **Point of Sale**: Customer billing and sales processing
- **Sales History**: View past transactions
- **Customer Lookup**: Basic customer information
- **Invoice Generation**: Print receipts and invoices

## Technical Features

### Database Support
- **MySQL**: Primary online database
- **SQLite**: Offline local database
- **Entity Framework Core**: ORM with migrations
- **Automatic Sync**: Background synchronization

### Security Features
- **Role-based permissions**: Granular access control
- **Session management**: Secure user sessions
- **Password hashing**: BCrypt password security
- **Access logging**: Audit trails for security

### Reporting System
- **Interactive Charts**: ApexCharts integration
- **Export Options**: PDF, Excel, CSV formats
- **Real-time Data**: Live dashboard updates
- **Custom Filters**: Date ranges, categories, products

### Tally Integration
- **Automatic Sync**: Customer, supplier, product data
- **Sales Export**: Transaction data to Tally
- **Purchase Import**: Purchase orders from Tally
- **Error Handling**: Sync status and error reporting

## Getting Started

### Prerequisites
- .NET 8.0 SDK
- MySQL Server
- Visual Studio 2022 or VS Code

### Database Setup
1. Install MySQL Server
2. Create database named `pharmacy`
3. Update connection string in `MauiProgram.cs`
4. Run the application to auto-create tables

### Running the Application
1. Clone the repository
2. Restore NuGet packages: `dotnet restore`
3. Build the solution: `dotnet build`
4. Run the application: `dotnet run`

### First Time Setup
1. The application will create the database schema automatically
2. Use one of the demo accounts to login
3. Explore features based on your role
4. Add your own users through Admin panel

## Navigation Security

The navigation menu dynamically shows/hides options based on user role:
- **Admin**: Sees all menu items
- **Manager**: No access to Reports or Settings sections
- **SalesPerson**: Limited to Sales operations only

## Development Notes

### Protected Pages
All pages inherit from role-specific base classes:
- `AdminOnlyPageBase`: Admin exclusive pages
- `ManagerAndAdminPageBase`: Admin and Manager access
- `AllRolesPageBase`: All authenticated users

### Permission Checking
```csharp
// In components
@if (CanAccess(UserRole.Admin, UserRole.Manager))
{
    // Content for Admin and Manager only
}

// In code
if (AuthService.HasPermission(UserRole.Admin))
{
    // Admin-only functionality
}
```

### Error Handling
- Unauthorized access redirects to `/unauthorized`
- Unauthenticated users redirect to `/login`
- Graceful error messages for role restrictions

## Future Enhancements
- Mobile app deployment (Android/iOS)
- Barcode scanning integration
- Advanced inventory forecasting
- Multi-location support
- API for third-party integrations
- Push notifications for stock alerts

## Support
For issues or questions, check the error logs and ensure proper database connectivity. The system includes comprehensive error handling and logging for troubleshooting.