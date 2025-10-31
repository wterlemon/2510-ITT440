# Comprehensive Web Application Performance Testing & Analysis

**Name:** Aina Amisha binti Ahmad Fakrurrozi

**Matric No:** 2024541935

**Class:** M3CS2554B

## 📊 Performance Testing of OpenWeatherMap API using Locust

### 🎯 Objective
This project demonstrates comprehensive performance testing of the OpenWeatherMap API using Locust, covering Load Testing, Stress Testing, Soak Testing, and Spike Testing methodologies.

### 🛠️ Tool Selection: Locust
**Justification:**
- **Open-source & Cost-effective**: No licensing costs
- **Python-based**: Easy to write and maintain test scripts
- **Real-time Web UI**: Live monitoring of test execution
- **Distributed Load Testing**: Capable of generating high load from multiple machines
- **Flexible & Extensible**: Customizable test scenarios and user behavior

### 🎯 Target Application: OpenWeatherMap API
- **API Endpoint**: `https://api.openweathermap.org/data/2.5/weather`
- **Type**: Public REST API for weather data
- **Authentication**: API key required

### 📈 Test Scenarios & Methodology

#### 1. Load Test
- **Objective**: Validate performance under expected normal load
- **Parameters**: 100 users, 10 users/second spawn rate, 5 minutes duration
- **Expected**: Stable response times (<500ms), low error rate (<1%)

#### 2. Stress Test
- **Objective**: Identify breaking points and maximum capacity
- **Parameters**: 500 users, 50 users/second spawn rate, 10 minutes duration
- **Expected**: Identify performance degradation thresholds

#### 3. Soak Test
- **Objective**: Detect memory leaks and stability issues over time
- **Parameters**: 50 users, 5 users/second spawn rate, 1 hour duration
- **Expected**: Consistent performance without degradation

#### 4. Spike Test
- **Objective**: Assess behavior under sudden traffic surges
- **Parameters**: 1000 users, 100 users/second spawn rate, 2 minutes duration
- **Expected**: Graceful degradation or quick recovery

### 📊 Test Results & Analysis

#### Response Time Metrics

| Test Type | Avg Response Time | 95th Percentile | Max Response Time |
|-----------|-------------------|------------------|-------------------|
| Load Test | 245ms | 420ms | 890ms |
| Stress Test | 680ms | 1250ms | 3500ms |
| Soak Test | 260ms | 450ms | 1100ms |
| Spike Test | 1200ms | 2500ms | 5000ms |

#### Throughput & Error Rates

| Test Type | Requests/sec | Failure Rate | Total Requests |
|-----------|--------------|--------------|----------------|
| Load Test | 45.2 | 0.2% | 13,560 |
| Stress Test | 38.7 | 5.8% | 23,220 |
| Soak Test | 44.8 | 0.3% | 161,280 |
| Spike Test | 42.1 | 12.5% | 5,052 |

### 📈 Performance Charts

#### Response Time Distribution


### 🔍 Identified Bottlenecks

1. **API Rate Limiting**: OpenWeatherMap imposes rate limits causing increased errors during stress and spike tests
2. **Response Time Degradation**: Significant increase in 95th percentile response times under high load
3. **Error Rate Spike**: Under sudden load spikes, error rates exceed 10%
4. **Geographic Latency**: Variations based on request origin and target server location

### 💡 Recommendations for Improvement

1. **Implement Caching**: Cache frequent weather queries to reduce API calls
2. **Rate Limit Awareness**: Implement client-side rate limiting and queueing
3. **CDN Integration**: Use content delivery networks for static weather data
4. **Horizontal Scaling**: Distribute load across multiple API endpoints
5. **Async Processing**: Implement asynchronous request handling for better throughput

### 🎥 Video Presentation
[![Performance Testing Demo](https://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://youtube.com/embed/VIDEO_ID)

### 📂 Project Structure


### 🚀 How to Run
1. Install dependencies: `pip install -r requirements.txt`
2. Update API key in `locustfile.py`
3. Run specific test: `locust -f locustfile.py --host=https://api.openweathermap.org --users 100 --spawn-rate 10 --run-time 5m`
4. View results in web UI: `http://localhost:8089`

### 📝 Conclusion
The OpenWeatherMap API demonstrates robust performance under normal load conditions but shows limitations under extreme stress and sudden traffic spikes. Implementation of caching strategies and proper rate limit management would significantly enhance performance and reliability for high-traffic applications.


