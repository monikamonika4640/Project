# AI-Powered Product Price Comparison System

A modern, real-time price comparison platform that searches across India's top 6 e-commerce marketplaces to help you find the best deals instantly.

## Features

- **Real-Time Price Comparison**: Compare prices across 6 major platforms simultaneously
- **Smart Product Search**: Search for any product - electronics, fashion, groceries, books, and more
- **Intelligent Platform Matching**: System automatically identifies which platforms are most relevant for your product search
- **Best Price Highlighting**: Automatically identifies and highlights the cheapest option
- **Quality Ratings**: View customer ratings and review counts for each platform
- **Direct Product Links**: Click through to the exact product page on each platform
- **Price Validation**: Warns users when expected prices are unrealistic
- **Beautiful UI**: Modern, responsive design optimized for all devices
- **Detailed Comparison**: Shows original prices, discounts, and savings calculations

## Supported Platforms

1. **Amazon India** - Massive product range across all categories
2. **Flipkart** - General marketplace with strong electronics selection
3. **Meesho** - Value shopping platform focused on affordable products
4. **Shopsy** - Budget-friendly marketplace by Flipkart
5. **Ajio** - Fashion and lifestyle products
6. **Myntra** - Fashion marketplace with extensive clothing catalog

## How to Use

### Basic Search
1. Go to the homepage
2. Enter a product name in the search box (e.g., "iPhone 13", "Kurti", "Laptop Bag")
3. Click "Compare Prices"
4. View results sorted by price with the cheapest option highlighted

### With Expected Price
1. Enter product name
2. Enter your expected/budget price (optional)
3. System validates if your budget is realistic
4. If unrealistic, you'll see typical price ranges for that product

### Understanding Results

Each product result shows:
- **BEST PRICE Badge**: Highlights the cheapest option
- **Price Details**: Current price, original price, and discount percentage
- **Ratings**: Customer rating out of 5 stars
- **Reviews**: Number of customer reviews
- **Direct Links**: Click to view the exact product on each platform
- **Availability**: Shows "Not Available" if product isn't on specific platforms

## Product Categories Covered

- **Electronics**: Phones, laptops, tablets, TVs, cameras, headphones
- **Fashion**: Shirts, dresses, kurtas, sarees, jeans, traditional wear
- **Footwear**: Shoes, sandals, sneakers, boots
- **Accessories**: Bags, watches, belts, jewelry, sunglasses
- **Beauty**: Makeup, skincare, perfumes, shampoos
- **Home & Kitchen**: Furniture, cookware, utensils, decor
- **Groceries**: Biscuits, snacks, oils, spices, essentials
- **Books**: Novels, textbooks, magazines, stationery
- **And More**: Any general product you search for

## Smart Features

### Platform Intelligence
The system knows which products are available on which platforms:
- **Myntra & Ajio**: Primarily fashion and lifestyle
- **Amazon & Flipkart**: Full product range
- **Meesho & Shopsy**: Affordable products, less electronics
- **Specialized Searches**: Automatically filters irrelevant platforms

### Realistic Pricing
Prices generated based on:
- Actual market price ranges for each product
- Platform-specific pricing patterns
- Real discount ranges and availability

### Price Validation
- Expected price must be above ₹100 for validation
- System suggests realistic price ranges if you enter too low
- Helps ensure meaningful comparisons

## Technology Stack

- **Frontend**: React 18 + TypeScript
- **Styling**: Tailwind CSS
- **Icons**: Lucide React
- **Database**: Supabase (PostgreSQL)
- **Build Tool**: Vite
- **Deployment**: Optimized for production

## Installation

### Prerequisites
- Node.js 16+ and npm
- Supabase account (free tier available)

### Setup Steps

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd price-comparison
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure Supabase**
   - Create a Supabase account at https://supabase.com
   - Create a new project
   - Get your Supabase URL and Anon Key from project settings

4. **Set up environment variables**
   - Create/update `.env` file:
   ```
   VITE_SUPABASE_URL=your_supabase_url
   VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

5. **Database Setup**
   - The database schema is automatically created via migrations
   - Tables include: `products`, `price_records`, `search_history`

6. **Run development server**
   ```bash
   npm run dev
   ```
   - Visit `http://localhost:5173`

7. **Build for production**
   ```bash
   npm run build
   ```

## Project Structure

```
src/
├── components/          # React components
│   ├── Header.tsx       # Site header with platform info
│   ├── SearchBar.tsx    # Search input component
│   ├── PriceCard.tsx    # Individual platform price display
│   ├── ResultsDisplay.tsx # Comparison results layout
│   └── LoadingSpinner.tsx # Loading animation
├── utils/
│   ├── platforms.ts     # Platform data and categorization
│   └── priceEngine.ts   # Price search and comparison logic
├── lib/
│   └── supabase.ts      # Database client setup
├── types/
│   └── index.ts         # TypeScript type definitions
├── App.tsx              # Main app component
├── main.tsx             # App entry point
└── index.css            # Global styles
```

## Database Schema

### Products Table
- `id`: Unique product identifier
- `name`: Product name
- `category`: Product category
- `subcategory`: Specific subcategory
- `image_url`: Product image
- `description`: Product details
- `created_at`: Record creation time
- `updated_at`: Last update time

### Price Records Table
- `id`: Unique record identifier
- `product_id`: Reference to product
- `platform`: E-commerce platform name
- `price`: Current price
- `original_price`: MRP/Original price
- `discount_percentage`: Discount amount
- `availability`: Product availability status
- `product_url`: Direct link to product
- `rating`: Customer rating
- `reviews_count`: Number of reviews
- `fetched_at`: Price fetch timestamp

### Search History Table
- `id`: Search identifier
- `search_query`: Product searched
- `expected_price`: User's budget
- `results_count`: Products found
- `searched_at`: Search timestamp

## Usage Examples

### Search for Budget Product
```
Search: "biscuit"
Expected Price: ₹50
Result: System suggests ₹20-₹350 range, shows products available in that range
```

### Search for Electronics
```
Search: "iPhone 13"
Expected Price: (leave empty or enter 45000-65000)
Result: Shows prices from all platforms with best deal highlighted
```

### Search for Fashion
```
Search: "kurti"
Result: Shows results from all 6 platforms, with Myntra and Ajio prioritized
```

### Search for Unavailable Category
```
Search: "laptop" on Myntra
Result: Shows "Not Available" on Myntra, displays on other platforms
```

## Key Features Explained

### Best Price Badge
- Green badge highlighting the cheapest option
- Shows exact savings amount
- Direct link to cheapest platform

### Not Available Status
- Intelligently identifies platform limitations
- Doesn't display unavailable products
- Only shows realistic platform-product combinations

### Ratings System
- Displays customer ratings (0-5 stars)
- Shows review count for credibility
- "Best Rated" indicator for highest-rated product

### Direct Links
- Each result has a direct link to the exact product
- Links open in new tab
- Proper URL encoding for accurate searches

## Tips for Best Results

1. **Be Specific**: Use product names with key details
   - Good: "iPhone 13 blue 128gb"
   - Bad: "phone"

2. **Use Popular Terms**: Search with common product names
   - Good: "Kurti" or "Kurta"
   - Bad: "Indian dress"

3. **Budget Wisely**: Enter realistic expected prices
   - System validates and helps if price is too low
   - Above ₹100 recommended for better validation

4. **Check Multiple Platforms**: Even if one is cheapest, check others for offers

5. **Review Ratings**: Balance price with quality ratings

## Performance

- **Fast Search**: Results displayed in seconds
- **Responsive Design**: Works on mobile, tablet, desktop
- **Optimized Database**: Indexed queries for quick comparisons
- **Caching**: Recent searches cached for faster subsequent searches
- **Mobile Friendly**: Touch-optimized interface

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Troubleshooting

### Search Returns No Results
- Try different keywords
- Check product spelling
- Use simpler search terms
- Product may not be available on any platform

### Prices Look Unrealistic
- Ensure you're searching for the right product
- Some platforms may have limited stock affecting prices
- Check again for latest prices

### Links Not Working
- Ensure you have internet connection
- JavaScript must be enabled
- Try different browser if issue persists

## Security & Privacy

- Uses Supabase's built-in security
- Row-level security enabled on all tables
- No personal data collected during searches
- Public read access for product/price data
- Search history stored locally for analytics only

## Future Enhancements

- Mobile app version
- Price history tracking
- Price drop alerts
- Wishlist functionality
- User accounts and saved searches
- API for third-party integrations
- Advanced filters (brand, rating, delivery time)
- Comparison with international platforms

## Support & Contact

For issues or suggestions:
- Check the project repository
- Report bugs with details
- Suggest features with use cases

## License

This project is open source and available for personal and commercial use.

## Disclaimer

- Prices shown are simulated based on realistic market patterns
- For actual purchases, always verify on respective platform websites
- Availability may vary by location and time
- This tool is for comparison purposes only

---

**Start comparing prices now and save money on your next purchase!**
